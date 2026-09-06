# ketesa

Agent-facing notes for this repository.

## Public repo hygiene

- The Forgejo repo is public. Never commit internal hostnames, LAN IPs,
  usernames, home paths, or credentials. Tracked files use placeholders
  (`<server-host>`, `<user>`, `~/...`); test fixtures use RFC 5737 documentation addresses (`192.0.2.x`); real service addresses never go in tracked files.

- Automated checks: git hooks in `~/.githooks` (installed via global
  `core.hooksPath`) block commits and pushes that match the hygiene pattern
  (LAN IPs, `.local` hostnames, `/home/<user>` paths). Legitimate matches
  (test fixtures, vendored code) belong in `.git/hygiene-excludes`.
- Manual scan of the tracked tree (what the pre-push hook checks):
  `source ~/.githooks/hygiene-lib.sh && hygiene_scan_tree HEAD`
