FROM python:3

# Install packages
RUN apt-get update
#RUN apt-get install -y jq tzdata python3 python3-dev python3-pip \
#        python3-six python3-pyasn1 libportaudio2 alsa-utils
RUN apt-get install -y jq tzdata  \
        python3-six python3-pyasn1 libportaudio2 alsa-utils
RUN pip3 install --upgrade pip six \
        google-assistant-library==1.0.1 google-auth==1.6.3 \
        requests_oauthlib cherrypy flask flask-jsonpify flask-restful \
        grpcio google-assistant-grpc==0.2.1 google-auth-oauthlib==0.3.0 googleapis-common-protos==1.6.0
RUN apt-get remove -y --purge python3-pip python3-dev && apt-get clean -y && rm -rf /var/lib/apt/lists/*

# Copy data
COPY run.sh *.py /
RUN chmod a+x /run.sh

ENTRYPOINT [ "/run.sh" ]
