FROM ubuntu:24.04

# Объединяем установку пакетов и очистку кеша в один слой
RUN apt-get update && apt-get install -y \
    python3 \
    python3-pip \
    && rm -rf /var/lib/apt/lists/*

# Установка flask
RUN pip3 install flask --break-system-packages

COPY app.py /opt/app.py

# Устанавливаем переменную окружения через ENV, чтобы не использовать shell в ENTRYPOINT
ENV FLASK_APP=/opt/app.py

# Используем JSON синтаксис (exec form) для корректной обработки сигналов (SIGTERM)
ENTRYPOINT ["flask", "run", "--host=0.0.0.0", "--port=5000"]
