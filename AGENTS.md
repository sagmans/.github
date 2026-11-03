# AGENTS.md

## Git hooks

After cloning, run `scripts/setup-hooks` once. It sets
`core.hooksPath=.githooks` for this clone and its worktrees. The hooks run the
generic checks: DCO sign-off, message structure, gitleaks secret scan, signed
commits on push, and signed annotated tags on push (`git tag -s`).

All checks must pass before a push. Never bypass them with `--no-verify` or any
other bypass. The files in `.githooks/` and `scripts/setup-hooks` are copies of
the dotf template (`templates/githooks/`); change them there, not here.

Commit with `git commit -s -S -m`. Tag with `git tag -s <tag> -m "<message>"`.

Commit messages follow `.githooks/GIT_CONVENTION.md`, which `commit-msg` and
`pre-push` enforce. The generic checks need gitleaks, osv-scanner, semgrep,
lizard and markdownlint-cli2, plus actionlint and zizmor when a push changes
workflow files. A missing tool blocks the hook.
