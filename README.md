# papa-channy/tap

Homebrew formulae for my public tools.

## Usage

```bash
brew tap papa-channy/tap
brew install <formula>
```

## Available formulae

### gdrive-organizer

AI-powered Google Drive organizer CLI — scan, classify with AI, review plans, dry-run, apply, rollback.

```bash
brew install papa-channy/tap/gdrive-organizer
gdrive-organizer --version
```

Upstream: [papa-channy/google-drive-manager](https://github.com/papa-channy/google-drive-manager)

---

## For maintainers — bumping a formula

When a new upstream release is published to PyPI:

1. Fetch the new sdist URL + sha256 from PyPI (`pip download --no-deps --no-binary :all: gdrive-organizer==<new-version>`)
2. Regenerate transitive resources:
   ```bash
   uv venv --python 3.12 /tmp/poet-env
   /tmp/poet-env/bin/python -m pip install 'setuptools<81' homebrew-pypi-poet gdrive-organizer==<new-version>
   /tmp/poet-env/bin/python -m poet -f gdrive-organizer 2>/dev/null
   ```
3. Copy the resource blocks into `Formula/gdrive-organizer.rb`; keep the existing `desc`, `homepage`, `license`, `depends_on`, and `test do` blocks
4. Verify:
   ```bash
   brew untap papa-channy/tap && brew tap papa-channy/tap
   brew uninstall gdrive-organizer 2>/dev/null; brew install papa-channy/tap/gdrive-organizer
   brew test papa-channy/tap/gdrive-organizer
   ```
5. Commit and push

## License

Formulae are under Apache-2.0 (matching the upstream project licenses where applicable). See each formula's `license` field for specifics.
