# Setup python and poetry

Composite GitHub Action that sets up Python via [`actions/setup-python`](https://github.com/actions/setup-python)
and installs [Poetry](https://python-poetry.org/).

Poetry is installed with [pipx](https://pipx.pypa.io/) into its own isolated environment, so it doesn't
interfere with project dependencies. Virtualenvs are created in `$GITHUB_WORKSPACE/.virtualenvs`.

## Usage

```yaml
steps:
  - uses: actions/checkout@v7
  - uses: xbabka01/poetry-action@main
    with:
      python_version: "3.13"
      poetry_version: "2.1.3"   # optional, latest if omitted
  - run: poetry install
```

## Inputs

| Name             | Required | Default | Description                                                                 |
|------------------|----------|---------|-----------------------------------------------------------------------------|
| `python_version` | yes      |         | Python version to set up                                                    |
| `poetry_version` | no       | `""`    | Poetry version (`2.1.3`) or pip specifier (`>=2,<3`). Latest if empty. |

## Outputs

| Name             | Description                  |
|------------------|------------------------------|
| `python_version` | The installed Python version |
