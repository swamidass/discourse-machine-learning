Discourse Machine Learning
==========================

An open source project that gives tools and utilities for applying machine learning tools to Discourse Forums (https://discourse.org).




Description
===========


Discourse is modern forum software for your community. Use it as a mailing list, discussion forum, long-form chat room, and more. It is becoming more widely used.  Discourse has a REST API based on JSON (https://docs.discourse.org/). Reading public data does not require authentication. Writing data does. It also has a webhook framework based on JSON (https://meta.discourse.org/t/setting-up-webhooks/49045).


This package's goal is to build:

1. Pipelines that interacts with Discourse's REST API to download and maintain data from a forum into structured data in a format suitable for machine learning and data mining.

3. A frameworks for specific tasks that interact with the local data store and Discourse to accomplish particular functions, guided by machine learning.

4. Implementations of machine learning (or data mining) powered tools that make use of these frameworks to do useful activities.


Roadmap
========

We are currently in pre-alpha stage, and are working with this initial roadmap.

1. Build initial implementation that enables snapshot of forum data using REST API. Backend may be plain text files or neo4j.
2. Build first framework, which will enable text analysis of forum posts.
3. Build first tool that uses framework to do simple textual analysis of forum posts using a simple data mining algorithm (e.g. Word Clouds).
4. Build first tool that uses more complex textual analysis using machine learning tools.
5. Assess project and decide next steps to add to roadmap.

Once we have a useful API and tools, we will refactor ensure good test coverage, and submit to PyPi.

Future Goals
============

- Support for multiple storage backends (e.g. cloud, text files, neo4j, postgres)
- Support for generating snapshots from Discourse database dumps/backups.
- Incremental update of data snapshots using the REST API (to the extent that this is possible)
- A REST server that interacts with Discourse's webhook framework to keep data repository snapshots up-to-date, and trigger particular actions.
- Configurability in what data is stored and included in the snapshots.
- Frameworks/tools for performing actions in discourse through the API (e.g. tagging topics and auto-moderation).

License
=========

MIT



Note
====

This project has been set up using PyScaffold 3.2.3. For details and usage
information on PyScaffold see https://pyscaffold.)



Note
====

This project has been set up using PyScaffold 3.2.3. For details and usage
information on PyScaffold see https://pyscaffold.)

## Installation

In order to set up the necessary environment:

1. create an environment `discourse-machine-learning` with the help of [conda],
   ```
   conda env create -f environment.yaml
   ```
2. activate the new environment with
   ```
   conda activate discourse-machine-learning
   ```
3. install `discourse-machine-learning` with:
   ```
   python setup.py install # or `develop`
   ```

Optional and needed only once after `git clone`:

4. install several [pre-commit] git hooks with:
   ```
   pre-commit install
   ```
   and checkout the configuration under `.pre-commit-config.yaml`.
   The `-n, --no-verify` flag of `git commit` can be used to deactivate pre-commit hooks temporarily.

5. install [nbstripout] git hooks to remove the output cells of committed notebooks with:
   ```
   nbstripout --install --attributes notebooks/.gitattributes
   ```
   This is useful to avoid large diffs due to plots in your notebooks.
   A simple `nbstripout --uninstall` will revert these changes.


Then take a look into the `scripts` and `notebooks` folders.

## Dependency Management & Reproducibility

1. Always keep your abstract (unpinned) dependencies updated in `environment.yaml` and eventually
   in `setup.cfg` if you want to ship and install your package via `pip` later on.
2. Create concrete dependencies as `environment.lock.yaml` for the exact reproduction of your
   environment with:
   ```
   conda env export -n discourse-machine-learning -f environment.lock.yaml
   ```
   For multi-OS development, consider using `--no-builds` during the export.
3. Update your current environment with respect to a new `environment.lock.yaml` using:
   ```
   conda env update -f environment.lock.yaml --prune
   ```
## Project Organization

```
├── AUTHORS.rst             <- List of developers and maintainers.
├── CHANGELOG.rst           <- Changelog to keep track of new features and fixes.
├── LICENSE.txt             <- License as chosen on the command-line.
├── README.md               <- The top-level README for developers.
├── configs                 <- Directory for configurations of model & application.
├── data
│   ├── external            <- Data from third party sources.
│   ├── interim             <- Intermediate data that has been transformed.
│   ├── processed           <- The final, canonical data sets for modeling.
│   └── raw                 <- The original, immutable data dump.
├── docs                    <- Directory for Sphinx documentation in rst or md.
├── environment.yaml        <- The conda environment file for reproducibility.
├── models                  <- Trained and serialized models, model predictions,
│                              or model summaries.
├── notebooks               <- Jupyter notebooks. Naming convention is a number (for
│                              ordering), the creator's initials and a description,
│                              e.g. `1.0-fw-initial-data-exploration`.
├── references              <- Data dictionaries, manuals, and all other materials.
├── reports                 <- Generated analysis as HTML, PDF, LaTeX, etc.
│   └── figures             <- Generated plots and figures for reports.
├── scripts                 <- Analysis and production scripts which import the
│                              actual PYTHON_PKG, e.g. train_model.
├── setup.cfg               <- Declarative configuration of your project.
├── setup.py                <- Use `python setup.py develop` to install for development or
|                              or create a distribution with `python setup.py bdist_wheel`.
├── src
│   └── discourse_machine_learning <- Actual Python package where the main functionality goes.
├── tests                   <- Unit tests which can be run with `py.test`.
├── .coveragerc             <- Configuration for coverage reports of unit tests.
├── .isort.cfg              <- Configuration for git hook that sorts imports.
└── .pre-commit-config.yaml <- Configuration of pre-commit git hooks.
```

## Note

This project has been set up using PyScaffold 3.2.3 and the [dsproject extension] 0.4.
For details and usage information on PyScaffold see https://pyscaffold.org/.

[conda]: https://docs.conda.io/
[pre-commit]: https://pre-commit.com/
[Jupyter]: https://jupyter.org/
[nbstripout]: https://github.com/kynan/nbstripout
[Google style]: http://google.github.io/styleguide/pyguide.html#38-comments-and-docstrings
[dsproject extension]: https://github.com/pyscaffold/pyscaffoldext-dsproject
