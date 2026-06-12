---
title: "W: Failed to fetch http://...... when using &quot;apt-get update&quot;"
date: 2013-07-05
forum: General Help
---

### Post by jannetyang on 2013-07-05
Hi:

when I try to install packages from the internet using "apt-get", I found that it can't get packages from the sources, and when I try "apt-get update", the error below occurs:
[U]
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring-backports/universe/i18n/Translation-en_HK](http://archive.ubuntu.com/ubuntu/dists/raring-backports/universe/i18n/Translation-en_HK)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.156 80]
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring-backports/universe/i18n/Translation-en](http://archive.ubuntu.com/ubuntu/dists/raring-backports/universe/i18n/Translation-en)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.156 80]
[/U]
I'm sure that the server is connected to the internet and there should be no network connection issue. because I can ping the source server as below:

[U]root@GU-Innova:/etc/apt# ping archive.ubuntu.com
PING archive.ubuntu.com (91.189.92.202) 56(84) bytes of data.
64 bytes from sudice.canonical.com (91.189.92.202): icmp_req=1 ttl=36 time=415 ms
64 bytes from sudice.canonical.com (91.189.92.202): icmp_req=2 ttl=36 time=423 ms
64 bytes from sudice.canonical.com (91.189.92.202): icmp_req=3 ttl=36 time=411 ms
64 bytes from sudice.canonical.com (91.189.92.202): icmp_req=4 ttl=36 time=423 ms[/U]
[U]^C
--- archive.ubuntu.com ping statistics ---
5 packets transmitted, 4 received, 20% packet loss, time 4000ms
rtt min/avg/max/mdev = 411.014/418.387/423.904/5.487 ms
root@GU-Innova:/etc/apt# ping 91.189.92.156
PING 91.189.92.156 (91.189.92.156) 56(84) bytes of data.
64 bytes from 91.189.92.156: icmp_req=1 ttl=35 time=412 ms
64 bytes from 91.189.92.156: icmp_req=2 ttl=35 time=414 ms
64 bytes from 91.189.92.156: icmp_req=3 ttl=35 time=414 ms
64 bytes from 91.189.92.156: icmp_req=4 ttl=35 time=404 ms
^C
--- 91.189.92.156 ping statistics ---
5 packets transmitted, 4 received, 20% packet loss, time 4004ms
rtt min/avg/max/mdev = 404.581/411.388/414.675/4.123 ms[/U]

Do any of you have any ideas? thank you very much!

---

### Post by claracc on 2013-07-05
First address: [http://archive.ubuntu.com/ubuntu/dists/raring-backports/universe/i18n/Translation-en_HK](http://archive.ubuntu.com/ubuntu/dists/raring-backports/universe/i18n/Translation-en_HK) gives back an 404 not found error since the url is not in the server.

Try to change the server to download software

---

