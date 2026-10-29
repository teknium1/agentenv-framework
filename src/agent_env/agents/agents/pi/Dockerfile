# docker build -t pi-a2a src/agent_env/agents/agents/pi
FROM mirror.gcr.io/library/ubuntu:24.04@sha256:24737cef17f4e22b1977df7d9a05e77c4e28b7da5b8911f8d8ccda136bf3573c
WORKDIR /app
# Named sources: agent-env packs the build context install/v1 copies from the COPY sources.
COPY a2a_server.py changelog.py install.sh peers.py pi_agent.py requirements.txt start.sh ./
RUN sh install.sh \
    && useradd --create-home agent \
    && mkdir /workspace \
    && chown agent /app /workspace
ENV PATH="/opt/pi-a2a-venv/bin:/opt/pi/bin:/opt/node/bin:${PATH}"
USER agent
EXPOSE 8000
CMD ["python3", "a2a_server.py"]
