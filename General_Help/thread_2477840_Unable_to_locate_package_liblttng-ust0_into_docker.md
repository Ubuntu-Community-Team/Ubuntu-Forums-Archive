---
title: "Unable to locate package liblttng-ust0 into docker image from ubuntu:22.04"
date: 2022-08-08
forum: General Help
---

### Post by jamiekt on 2022-08-08
I have inherited a Dockerfile that is built `FROM ubuntu:20.18`. I've been tasked with upgrading this to the latest available version of ubuntu, 22.04. Unfortunately my attempts to build on ubunto:22.04 fail with error:

> => ERROR [ 3/19] RUN DEBIAN_FRONTEND=noninteractive apt-get update &&     apt-get install -y         curl         unzip         ca-certificates         software-properties-common         sudo         su  2.6s
------                                                                                                                                                                                                            
 > [ 3/19] RUN DEBIAN_FRONTEND=noninteractive apt-get update &&     apt-get install -y         curl         unzip         ca-certificates         software-properties-common         sudo         supervisor         jq         iputils-ping         build-essential         zlib1g-dev         gettext         liblttng-ust0         libcurl4-openssl-dev         openssh-client         python3-pip &&     rm -rf /var/lib/apt/lists/* &&     apt-get clean:                                                                                                                                                                                        
#7 0.484 Hit:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy InRelease                                                                                                                                                   
#7 0.484 Hit:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security InRelease                                                                                                                                         
#7 0.554 Hit:3 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates InRelease
#7 0.642 Hit:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-backports InRelease
#7 0.918 Reading package lists...
#7 1.662 Reading package lists...
#7 2.394 Building dependency tree...
#7 2.542 Reading state information...
#7 2.554 E: Unable to locate package liblttng-ust0
------
executor failed running [/bin/sh -c DEBIAN_FRONTEND=noninteractive apt-get update &&     apt-get install -y         curl         unzip         ca-certificates         software-properties-common         sudo         supervisor         jq         iputils-ping         build-essential         zlib1g-dev         gettext         liblttng-ust0         libcurl4-openssl-dev         openssh-client         python3-pip &&     rm -rf /var/lib/apt/lists/* &&     apt-get clean]: exit code: 100




Here is my Dockerfile:

```
FROM ubuntu:22.04




RUN DEBIAN_FRONTEND=noninteractive apt-get update && apt-get install -y apt-transport-https




RUN DEBIAN_FRONTEND=noninteractive apt-get update && \
    apt-get install -y \
        curl \
        unzip \
        ca-certificates \
        software-properties-common \
        sudo \
        supervisor \
        jq \
        iputils-ping \
        build-essential \
        zlib1g-dev \
        gettext \
        liblttng-ust0 \
        libcurl4-openssl-dev \
        openssh-client \
        python3-pip && \
    rm -rf /var/lib/apt/lists/* && \
    apt-get clean

```


If I change to `[COLOR=#569CD6][FONT=Menlo]FROM[/FONT][/COLOR][COLOR=#D4D4D4][FONT=Menlo] ubuntu:20.04[/FONT][/COLOR]` then it succeeds.

I have found an article [https://linux-packages.com/ubuntu-jammy-jellyfish/package/liblttng-ust0](https://linux-packages.com/ubuntu-jammy-jellyfish/package/liblttng-ust0)  that suggests liblttng-ust0 should be available for ubuntu:22.04. Can anyone suggest what the problem might be?

---

### Post by Holger_Gehrke on 2022-08-08
If you do a [search for 'lttng-ust' on packages.ubuntu.com]("https://packages.ubuntu.com/search?keywords=lttng-ust&searchon=names&suite=jammy&section=all") you'll find that the packages is named liblttng-ust1. Seems like the name has changed slightly (probably a major revision ...).

---

### Post by jamiekt on 2022-08-08
> **Holger_Gehrke said:**
> If you do a [search for 'lttng-ust' on packages.ubuntu.com]("https://packages.ubuntu.com/search?keywords=lttng-ust&searchon=names&suite=jammy&section=all") you'll find that the packages is named liblttng-ust1. Seems like the name has changed slightly (probably a major revision ...).

Excellent, thank you very much. You are quite correct.

I see:
[LIST]
[*]for impish it is called liblttng-ust0 [https://packages.ubuntu.com/search?keywords=lttng-ust&searchon=names&suite=impish&section=all](https://packages.ubuntu.com/search?keywords=lttng-ust&searchon=names&suite=impish&section=all)
[*]for jammy it is called liblttng-ust1 [https://packages.ubuntu.com/search?keywords=lttng-ust&searchon=names&suite=jammy&section=all](https://packages.ubuntu.com/search?keywords=lttng-ust&searchon=names&suite=jammy&section=all)
[/LIST]

Very much appreciated, thank you again.

---

