FROM evalai_django

RUN apt-get update && \
  apt-get install -q -y default-jdk

RUN pip install -U cffi service_identity cython==0.29 numpy==1.14.5
RUN pip install -r worker.txt
RUN pip install torch --no-cache-dir

ADD . /code

CMD ["./docker/wait-for-it.sh", "django:8000", "--", "python", "-m", "scripts.workers.submission_worker"]
