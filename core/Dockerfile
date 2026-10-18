FROM python:3.12-slim

# Install system and compilation dependencies for h5py, mysql, and science packages
RUN apt-get update && apt-get install -y \
    build-essential \
    pkg-config \
    default-libmysqlclient-dev \
    libhdf5-dev \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /app

COPY requirements.txt /app/

RUN python -m pip install --upgrade pip
# Use pre-compiled binary wheels where available to avoid building from source
RUN pip install --no-cache-dir --prefer-binary -r requirements.txt

COPY . /app/

EXPOSE 8000
CMD ["python", "manage.py", "runserver", "0.0.0.0:8000"]