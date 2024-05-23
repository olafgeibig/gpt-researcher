
ARG VARIANT=3-bookworm
ARG USER=vscode

FROM mcr.microsoft.com/vscode/devcontainers/python:${VARIANT}

RUN apt-get update \
    && apt-get satisfy -y \
    "chromium, chromium-driver (>= 115.0)" \
    && chromium --version && chromedriver --version

RUN apt-get update \
    && apt-get install -y --fix-missing firefox-esr wget \
    && wget https://github.com/mozilla/geckodriver/releases/download/v0.33.0/geckodriver-v0.33.0-linux64.tar.gz \
    && tar -xvzf geckodriver* \
    && chmod +x geckodriver \
    && mv geckodriver /usr/local/bin/

# RUN pip install -r requirements.txt

# RUN useradd -ms /bin/bash gpt-researcher \
#     && chown -R gpt-researcher:gpt-researcher /usr/src/app

# USER $USER

# COPY --chown=$USER:$USER ./ ./

EXPOSE 8000
CMD ["uvicorn", "main:app", "--host", "0.0.0.0", "--port", "8000"]

