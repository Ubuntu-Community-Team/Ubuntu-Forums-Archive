---
title: "Running transmission-daemon as user nobody"
date: 2015-02-25
forum: General Help
---

### Post by kstenerud on 2015-02-25
I'm trying to set up a docker image for transmission-daemon, and I'm stuck at the last point, which is getting transmission-daemon to run as user "nobody".

"Why", you ask? Because user "nobody" is the only user with a consistent UID inside and outside of the container, and I want files created by Transmission via my volume mount to have a deterministic owner user and group. If I don't do this, inside the container it runs as user 103 (debian-transmission), group 106 (debian-transmission), which in my case happen to map outside of the container as "dnsmasq" and "kvm" whenever it writes to the mounted volume. Not a desirable outcome. "nobody" and "nogroup", on the other hand, always map to 65534 both inside and outside of the container.

That said, I have run apt-get install transmission-daemon, then recursively changed ownership of /etc/transmission-daemon and /var/lib/transmission-daemon to "nobody". I've also changed the user to "nobody" in /etc/init/transmission-daemon.conf, /etc/init.d/transmission-daemon, and /lib/systemd/system/transmission-daemon.service. It seems that only /etc/init.d/transmission-daemon is actually used, because once I change that over to use "nobody", calling "service transmission-daemon start" gives me the result "fail". No logs, no messages. Just "fail".

For reference, here is the actual Dockerfile I'm working on. If you remove the chown commands and the last sed command (for /etc/init.d/transmission-daemon), the daemon starts normally (but has the broken UID and GID). 00_transmission.sh is just a script that calls "service transmission-daemon start".

Dockerfile:
```
FROM phusion/baseimage
MAINTAINER Karl Stenerud <kstenerud@gmail.com>

RUN rm -rf /etc/service/sshd /etc/my_init.d/00_regen_ssh_host_keys.sh && \
    apt-get update && \
    apt-get install -y transmission-daemon && \
    apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

RUN cp /etc/init/transmission-daemon.conf /docker.tmp && \
    cat /docker.tmp | \
       sed 's/setuid debian-transmission/setuid nobody/g' | \
       sed 's/setgid debian-transmission/setgid nogroup/g' >/etc/init/transmission-daemon.conf && \
    rm /docker.tmp

RUN cp /etc/transmission-daemon/settings.json /docker.tmp && \
    cat /docker.tmp | \
       sed 's/"peer-port": 51413/"peer-port": 51043/g' | \
       sed 's/"rpc-password": "transmission"/"rpc-password": "mynewpassword",\n"rpc-whitelist-enabled": false/g' >/etc/transmission-daemon/settings.json && \
    rm /docker.tmp

RUN cp /lib/systemd/system/transmission-daemon.service /docker.tmp && \
    cat /docker.tmp | \
       sed 's/User=debian-transmission/User=nobody/g' > /lib/systemd/system/transmission-daemon.service && \
    rm /docker.tmp

# Remove this and the three chown commands and it works aside from the UID & GID issue
RUN cp /etc/init.d/transmission-daemon /docker.tmp && \
    cat /docker.tmp | \
       sed 's/USER=debian-transmission/USER=nobody/g' > /etc/init.d/transmission-daemon && \
    rm /docker.tmp

RUN chown root:root /etc/transmission-daemon
RUN chown -R nobody:nogroup /var/lib/transmission-daemon/*
RUN chown -R nobody:nogroup /etc/transmission-daemon/*

COPY 00_transmission.sh /etc/my_init.d/00_transmission.sh

VOLUME ["/var/lib/transmission-daemon/downloads"]
EXPOSE 9091
EXPOSE 12345

```

00_transmission.sh:
```
#!/bin/bash

service transmission-daemon start
```

---

### Post by kstenerud on 2015-02-26
Figured out the problem. It turns out that you MUST run the chown commands in the SAME run command as the apt-get. I have no idea why that works and running them as separate commands doesn't.

---

