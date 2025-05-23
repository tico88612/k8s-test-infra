# test-infra

[![GoDoc](https://godoc.org/k8s.io/test-infra?status.svg)](https://godoc.org/k8s.io/test-infra)
[![Build status](https://prow.k8s.io/badge.svg?jobs=ci-test-infra-continuous-test)](https://testgrid.k8s.io/sig-testing-misc#continuous)

This repository contains tools and configuration files for the testing and
automation needs of the Kubernetes project.

Our [architecture diagram](docs/architecture.svg) provides an (updated [#13063])
overview of how the different tools and services interact.

## CI Job Management

Kubernetes uses a [`prow`] instance at [prow.k8s.io] to handle CI and 
automation for the entire project. Everyone can participate in a 
self-service PR-based workflow, where changes are automatically deployed
after they have been reviewed. All job configs are located in [`config/jobs`]

- [Add or update job configs](/config/jobs/README.md#adding-or-updating-jobs)
- [Delete job configs](/config/jobs/README.md#deleting-jobs)
- [Test job configs locally](/config/jobs/README.md#testing-jobs-locally)
- [Trigger jobs on PRs using bot commands](https://go.k8s.io/bot-commands)

## Dashboards

### Test Result Dashboards

- [Testgrid](https://testgrid.k8s.io) shows historical test results over time ([`testgrid`])
- [Triage](https://go.k8s.io/triage) shows clusters of similar test failures across all jobs ([`triage`](/triage))

### Job and PR Dashboards

- [Deck](https://prow.k8s.io) shows what jobs are running or have recently run in prow ([`prow/cmd/deck`])
- [Gubernator's PR Dashboard](https://gubernator.k8s.io/pr) shows which PRs need your review ([`gubernator`])
- [PR Status](https://prow.k8s.io/pr) shows what needs to be done to get PRs matching a GitHub Query to merge ([`prow/cmd/tide`])
- [Tide History](https://prow.k8s.io/tide-history) shows what actions tide has taken over time to trigger tests and merge PRs ([`prow/cmd/tide`])
- [Tide Status](https://prow.k8s.io/tide) shows what PRs are in tide pools to be tested and merged ([`prow/cmd/tide`])

## Other Tools

- [`boskos`](/boskos) manages pools of resources; our CI leases GCP projects from these pools
- [`experiment`](/experiment) is a catchall directory for one-shot tools or scripts
- [`gcsweb`](/gcsweb) is a UI we use to display test artifacts stored in public GCS buckets
- [`ghproxy`](/ghproxy) is a GitHub-aware reverse proxy cache to help keep our GitHub API token usage within rate limits
- [`gopherage`](/gopherage) is a tool for manipulating Go coverage files
- [`label_sync`](/label_sync) creates, updates and migrates GitHub labels across orgs and repos based on `labels.yaml` file
- [`kettle`](/kettle) extracts test results from GCS and puts them into bigquery
- [`kubetest`](/kubetest) is how our CI creates and e2e tests kubernetes clusters
- [`metrics`](/metrics) runs queries against bigquery to generate metrics based on test results
- [`robots/commenter`](/robots/commenter) is used by some of our jobs to comment on GitHub issues

## Contributing

Please see [CONTRIBUTING.MD](CONTRIBUTING.md)

[test-infra oncall]: https://go.k8s.io/oncall
[@k8s-ci-robot]: (https://github.com/k8s-ci-robot)
[#13063]: https://github.com/kubernetes/test-infra/issues/13063
[prow.k8s.io]: https://prow.k8s.io
[kubernetes/kubernetes]: https://github.com/kubernetes/kubernetes

[bot commands]: https://go.k8s.io/bot-commands
[`config/jobs`]: /config/jobs
[`gubernator`]: /gubernator
[`metrics`]: /metrics
[`prow`]: https://github.com/kubernetes-sigs/prow
[`prow/cmd/tide`]: https://github.com/kubernetes-sigs/prow/tree/main/cmd/tide
[`prow/cmd/deck`]: https://github.com/kubernetes-sigs/prow/tree/main/cmd/deck
[`testgrid`]: /testgrid
[testgrid.k8s.io]: https://testgrid.k8s.io
[`triage`]: /triage
