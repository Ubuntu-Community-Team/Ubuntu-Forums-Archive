---
title: "Ubuntu 16.04 : Error “Could not connect to archive.ubuntu.com:80 (91.189.88.152)”"
date: 2021-05-11
forum: General Help
---

### Post by manoj89 on 2021-05-11
**[Ubuntu 16.04 : Error “Could not connect to archive.ubuntu.com:80 (91.189.88.152)” while running “apt-get update ” command in a dockerfile]("https://stackoverflow.com/questions/67487156/ubuntu-16-04-error-could-not-connect-to-archive-ubuntu-com80-91-189-88-152")**

[COLOR=#242729][FONT=system-ui]I will put across my issue as follows :1
[/FONT][/COLOR]
[LIST=1]
[*]I want to build a docker image for Hyperledger Indy-sdk
[*]While building docker image it uses docker-compose command to build two images and combine them i.e., indy-pool image and getting-started image. My docker-compose.yml file looks as shown below
[/LIST]
[FONT=inherit]
#
version: '2'
services:
  indy_pool:
    build:
      context: ../../ci/
      dockerfile: indy-pool.dockerfile
      args:
        pool_ip: '10.0.0.2'
    image: indy_pool
    container_name: indy_pool
    working_dir: /home/indy
    ports:
      - "9701:9701"
      - "9702:9702"
      - "9703:9703"
      - "9704:9704"
      - "9705:9705"
      - "9706:9706"
      - "9707:9707"
      - "9708:9708"
    networks:
      pool_network:
        ipv4_address: 10.0.0.2
    volumes:
       - sandbox:/var/lib/indy/sandbox/
  jupyter:
    build:
      context: .
      dockerfile: getting-started.dockerfile
    command: jupyter notebook --ip=0.0.0.0
    image: getting-started
    container_name: getting_started
    working_dir: /home/indy
    volumes:
       - ./getting-started.ipynb:/home/indy/getting-started.ipynb
       - sandbox:/home/indy/sandbox
    ports:
      - "8888:8888"
    networks:
      - pool_network
    links:
      - indy_pool
networks:
  pool_network:
    driver: bridge
    ipam:
      driver: default
      config:
        -
          subnet: 10.0.0.0/24
volumes:
     sandbox:#
[/FONT]
3. The above docker-compose will initiate the indy-pool.dockerfile to run. The contents of indy-pool.dockerfile is as shown below[FONT=inherit]
[/FONT][FONT=inherit]
[/FONT]
#
FROM ubuntu:16.04


ARG uid=1000


# Install environment 
RUN apt-get update -y && apt-get install -y \
    git \
    wget \
    python3.5 \
    python3-pip \
    python-setuptools \
    python3-nacl \
    apt-transport-https \
    ca-certificates \
    supervisor


RUN pip3 install -U \
    pip==9.0.3 \
    setuptools


RUN apt-key adv --keyserver keyserver.ubuntu.com --recv-keys CE7709D068DB5E88 || \
    apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys CE7709D068DB5E88
ARG indy_stream=master
RUN echo "deb [https://repo.sovrin.org/deb](https://repo.sovrin.org/deb) xenial $indy_stream" >> /etc/apt/sources.list


RUN useradd -ms /bin/bash -u $uid indy


ARG indy_plenum_ver=1.12.1~dev989
ARG indy_node_ver=1.12.1~dev1172
ARG python3_indy_crypto_ver=0.4.5
ARG indy_crypto_ver=0.4.5
ARG python3_pyzmq_ver=18.1.0
ARG python3_orderedset_ver=2.0
ARG python3_psutil_ver=5.4.3
ARG python3_pympler_ver=0.5


RUN apt-get update -y && apt-get install -y \
        python3-pyzmq=${python3_pyzmq_ver} \
        indy-plenum=${indy_plenum_ver} \
        indy-node=${indy_node_ver} \
        python3-indy-crypto=${python3_indy_crypto_ver} \
        libindy-crypto=${indy_crypto_ver} \
        python3-orderedset=${python3_orderedset_ver} \
        python3-psutil=${python3_psutil_ver} \
        python3-pympler=${python3_pympler_ver} \
        vim


RUN echo "[supervisord]\n\
logfile = /tmp/supervisord.log\n\
logfile_maxbytes = 50MB\n\
logfile_backups=10\n\
logLevel = error\n\
pidfile = /tmp/supervisord.pid\n\
nodaemon = true\n\
minfds = 1024\n\
minprocs = 200\n\
umask = 022\n\
user = indy\n\
identifier = supervisor\n\
directory = /tmp\n\
nocleanup = true\n\
childlogdir = /tmp\n\
strip_ansi = false\n\
\n\
[program:node1]\n\
command=start_indy_node Node1 0.0.0.0 9701 0.0.0.0 9702\n\
directory=/home/indy\n\
stdout_logfile=/tmp/node1.log\n\
stderr_logfile=/tmp/node1.log\n\
\n\
[program:node2]\n\
command=start_indy_node Node2 0.0.0.0 9703 0.0.0.0 9704\n\
directory=/home/indy\n\
stdout_logfile=/tmp/node2.log\n\
stderr_logfile=/tmp/node2.log\n\
\n\
[program:node3]\n\
command=start_indy_node Node3 0.0.0.0 9705 0.0.0.0 9706\n\
directory=/home/indy\n\
stdout_logfile=/tmp/node3.log\n\
stderr_logfile=/tmp/node3.log\n\
\n\
[program:node4]\n\
command=start_indy_node Node4 0.0.0.0 9707 0.0.0.0 9708\n\
directory=/home/indy\n\
stdout_logfile=/tmp/node4.log\n\
stderr_logfile=/tmp/node4.log\n"\
>> /etc/supervisord.conf


USER indy


RUN awk '{if (index($1, "NETWORK_NAME") != 0) {print("NETWORK_NAME = \"sandbox\"")} else print($0)}' /etc/indy/indy_config.py> /tmp/indy_config.py
RUN mv /tmp/indy_config.py /etc/indy/indy_config.py


ARG pool_ip=127.0.0.1


RUN generate_indy_pool_transactions --nodes 4 --clients 5 --nodeNum 1 2 3 4 --ips="$pool_ip,$pool_ip,$pool_ip,$pool_ip"


EXPOSE 9701 9702 9703 9704 9705 9706 9707 9708


CMD ["/usr/bin/supervisord"]

#

4. [COLOR=#242729][FONT=system-ui]Now both Ubuntu 16.04 image and indy-pool image will get created successfully as shown in the image

[/FONT][/COLOR][IMG]https://i.stack.imgur.com/tlyQA.png[/IMG]


5.  [COLOR=#242729][FONT=inherit]After this when getting-started.dockerfile starts running. getting-started.dockerfile looks like this

#
[/FONT][/COLOR]FROM ubuntu:16.04


RUN useradd -ms /bin/bash indy


# Install environment
RUN  apt-get update -y &&   apt-get install -y \
    wget \
    python3.5 \
    python3-pip \
    python-setuptools \
    apt-transport-https \
    ca-certificates \
    software-properties-common


WORKDIR /home/indy


RUN pip3 install -U \
    pip \
    ipython-notebook \
      ipython==7.9 \
    setuptools \
    jupyter \
    python3-indy==1.11.0


RUN apt-key adv --keyserver keyserver.ubuntu.com --recv-keys CE7709D068DB5E88 \
    && add-apt-repository "deb [https://repo.sovrin.org/sdk/deb](https://repo.sovrin.org/sdk/deb) xenial stable" \
    && apt-get update \
    && apt-get install -y \
    libindy=1.11.0


USER indy


EXPOSE 8888
[COLOR=#242729][FONT=inherit]#
 [/FONT][/COLOR]
[LIST=1]
[*]The whole issue starts when RUN apt-get update -y gets executed in getting-started.dockerfile. The following lines of error are shown to me
[/LIST]
[FONT=inherit]
#
Err:6 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial InRelease
  Could not connect to archive.ubuntu.com:80 (91.189.88.152), connection timed out [IP: 91.189.88.152 80]
Err:7 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates InRelease
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.152 80]
Err:8 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports InRelease
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.152 80]
Fetched 3168 kB in 4min 0s (13.2 kB/s)
Reading package lists...
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/xenial/InRelease](http://archive.ubuntu.com/ubuntu/dists/xenial/InRelease)  Could not connect to archive.ubuntu.com:80 (91.189.88.152), connection timed out [IP: 91.189.88.152 80]
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/xenial-updates/InRelease](http://archive.ubuntu.com/ubuntu/dists/xenial-updates/InRelease)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.152 80]
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/xenial-backports/InRelease](http://archive.ubuntu.com/ubuntu/dists/xenial-backports/InRelease)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.152 80]


#

[COLOR=#242729][FONT=system-ui]**Note : My docker engine and docker-compose are installed on top of Ubuntu 20.04**[/FONT][/COLOR]
[COLOR=#242729][FONT=system-ui]To resolve this issue I went through multiple resources available in internet. From that I can say it is not an issue with DNS lookup and http proxy(as I am not working in proxy network). As I am new to Docker build and docker compose I strongly believe that it is something to do with image building process. If anyone of you have come across similar issue and resolved it kindly provide me suggestions to solve above one.[/FONT][/COLOR]
[/FONT]

---

