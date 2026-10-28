# Pogorelov Labs fork

This is an independently maintained, source-only preview of
[LearnHarness](https://github.com/amosblomqvist/learnharness). It is not an
official upstream release. The original project and its contributors created
the application; this fork retains their history and the AGPL-3.0 license.

## Provenance

The initial integration starts from upstream `main` at
[`3dd52110bbcbcba81645453ce0a8fdc230594c47`](https://github.com/amosblomqvist/learnharness/commit/3dd52110bbcbcba81645453ce0a8fdc230594c47)
(after the 0.3.9 release). The following proposed changes were merged into the
fork with their Git history intact. They remain separate, open upstream pull
requests; their inclusion here does not mean upstream has accepted them.

| Upstream PR | Integrated head | Change |
| --- | --- | --- |
| [#201](https://github.com/amosblomqvist/learnharness/pull/201) | [`35263dc`](https://github.com/ruspg/learnharness/commit/35263dce5d645c68b5453b919a85451da757b600) | Exa as an optional web research provider. |
| [#203](https://github.com/amosblomqvist/learnharness/pull/203) | [`b75e2f0`](https://github.com/ruspg/learnharness/commit/b75e2f06bbc4603b75f7a21bbb54550aff36eee1) | OpenAI Platform API dictation alongside Deepgram. |
| [#204](https://github.com/amosblomqvist/learnharness/pull/204) | [`75fe1df`](https://github.com/ruspg/learnharness/commit/75fe1df10bbdc222fefd221fdba307f1671c8772) | GPT-6.1 Terra support where available to the connected account. |
| [#205](https://github.com/amosblomqvist/learnharness/pull/205) | [`b2437b8`](https://github.com/ruspg/learnharness/commit/b2437b865c9d6f52b8740c735123f7a256c1a975) | Account-scoped ChatGPT context limits and an optional per-model override. |

The dictation and context changes include a shared settings-write fix and
regression tests for overlapping edits. When upstream incorporates a change,
reconcile the fork against that implementation and its history rather than
blindly applying the same fix twice.

## Scope and limitations

- ChatGPT model availability and context limits are determined by the connected
  account and provider. A larger advertised context window is not a guarantee
  for every account or request. The separate compaction threshold defaults to
  150,000 tokens and can be adjusted in Settings.
- OpenAI dictation requires an OpenAI Platform API key and is billed separately
  from a ChatGPT subscription. Exa research requires an Exa key and follows
  Exa's billing and usage limits.
- This stage publishes source only. It does not publish a Pogorelov Labs
  installer or update feed. Upstream's download links and existing desktop
  packaging configuration still belong to upstream and must not be presented
  as a release of this fork.
- Before distributing a forked desktop build, give it a separate app identity
  and data directory, configure its own update path and signing, and test
  sign-in, existing-data migration, and microphone permissions. Do not share
  or commit private credentials.

## Development and CI

Use the upstream development instructions in the [README](../README.md) and
[development guide](development.md). CI uses standard GitHub-hosted runners
for the public repository; the shared Pogorelov Labs VPS runners are not used
for this workflow. External fork pull-request workflows require maintainer
approval. Review workflow changes before approving them, since a pull request
can change which runner it requests.

The fork is intended to track upstream. Check upstream changes and the four
pull requests before updating the integrated branch; rerun the relevant tests
and review any overlapping changes.
