# syntax=docker/dockerfile:1

FROM python:{{cookiecutter.minor_python_version}}-slim-buster

ENV POETRY_VERSION=1.4 \
    POETRY_VIRTUALENVS_CREATE=false

# Install poetry
RUN pip install "poetry==$POETRY_VERSION"

# Copy only requirements to cache them in docker layer
WORKDIR /code
COPY poetry.lock pyproject.toml /code/

# Project initialization:
RUN poetry install --no-interaction --no-ansi --no-root --no-dev

# Copy Python code to the Docker image
COPY {{cookiecutter.project_slug}} /code/{{cookiecutter.project_slug}}/

CMD [ "python", "{{cookiecutter.project_slug}}/foo.py"]
