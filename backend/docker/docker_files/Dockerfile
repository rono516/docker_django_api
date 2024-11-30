FROM python:3.10

ENV PYTHONUNBUFFERED 1
ENV PYTHONDONTWRITEBYTECODE 1

# Install required dependencies
RUN set -e; \
    apt-get update; \
    apt-get -y install netcat-openbsd gettext; \
    apt-get clean;

RUN mkdir /code
COPY . /code/
WORKDIR /code

# Copy the entrypoint file explicitly
COPY ./docker/entrypoints/entrypoint.sh /code/docker/entrypoints/entrypoint.sh

# Upgrade pip and install requirements
RUN set -e; \
    /usr/local/bin/python -m pip install --upgrade pip; \
    python -m pip install -r /code/requirements.txt; \
    chmod +x /code/docker/entrypoints/entrypoint.sh;

EXPOSE 8000
ENTRYPOINT ["/code/docker/entrypoints/entrypoint.sh"]

# FROM python:3.10

# ENV PYTHONUNBUFFERED 1
# ENV PYTHONDONTWRITEBYTECODE 1

# RUN set -e; \
#     apt-get update ;\
#     apt-get -y install netcat ;\
#     apt-get -y install gettext ;

# RUN mkdir /code
# COPY . /code/
# WORKDIR /code

# RUN set -e; \
#     /usr/local/bin/python -m pip install --upgrade pip ;\
#     python -m pip install -r /code/requirements.txt ;\
#     chmod +x /code/docker/entrypoints/entrypoint.sh ;

# EXPOSE 8000
# ENTRYPOINT ["/code/docker/entrypoints/entrypoint.sh"]


