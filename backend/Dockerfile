# Example for a Debian-based image
FROM python:3.12-slim-bookworm

# 1. Fix for pyzbar (requires libzbar-dev)
# 2. Fix for OpenCV (requires libgl1-mesa-glx)
RUN apt-get update && \
    apt-get install -y libzbar-dev libgl1-mesa-glx && \
    rm -rf /var/lib/apt/lists/*

# The rest of your Dockerfile steps...
WORKDIR /app
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt
COPY . .

CMD ["sh", "-c", "uvicorn main:app --host 0.0.0.0 --port $PORT"]
