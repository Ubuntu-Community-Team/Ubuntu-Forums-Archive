---
title: "Not getting network connection after autoremove"
date: 2019-06-04
forum: General Help
---

### Post by monikashah on 2019-06-04
Dear Sirs,

I am using Ubuntu 18.04 and everything was working fine.


I have removed all java versions, and remove java 7. Thereafter, downloading eclipse packages was in progress and [COLOR=#ff0000]s[/COLOR][COLOR=#FF0000]uddenly  my network got disconnected. After that , I am not able to get any LAN/WIFI/USB tether network.
[/COLOR]
Please help me to resolve this issue.

Command sequence applied is mentioned below for your reference.
> sudo apt-get autoremove openjdk-8-jre> sudo apt-get autoremove openjdk-7-jre
> sudo apt-get autoremove openjdk-8-jdk
> sudo apt-get autoremove openjdk-7-jdk
> sudo apt-get install openjdk-7-jdk
> sudo apt-get install openjdk-7-jre
> sudo gedit /etc/environment
  type JAVA_HOME=/usr/lib/jvm/java-7-openjdk-amd64/
> source /etc/environment

---

### Post by TheFu on 2019-06-04
Call your ISP.
Java has nothing at all to do with networking.

---

### Post by monikashah on 2019-06-12
When I reinstall Ubuntu, it started working.
That means it should not be ISP problem.

This happen to me 2-3 times in same week.

---

### Post by &amp;wP*!) on 2019-06-13
autoremove deleted some dependencies related to OpenJDK which is used by some wireless drivers/applications.
This is the only explanation I can find.

Anyway, a fresh reinstall apparently solved  the problem.

Please set the thread to SOLVED

---

### Post by garvinrick4 on 2019-06-13
Please feel free to ask for all the help you need and don't feel bad about any answer we were all where you are with linux at one time.
Most users recognize someone new to linux and want to help.


 Is basically where your internet connection exists
open a terminal and type this
> gedit /etc/resolv.conf

Here is mine look on bottom does yours have your internet supplier

# This file is managed by man:systemd-resolved(8). Do not edit.
#
# This is a dynamic resolv.conf file for connecting local clients to the
# internal DNS stub resolver of systemd-resolved. This file lists all
# configured search domains.
#
# Run "systemd-resolve --status" to see details about the uplink DNS servers
# currently in use.
#
# Third party programs must not access this file directly, but only through the
# symlink at /etc/resolv.conf. To manage man:resolv.conf(5) in a different way,
# replace this symlink by a static file or a different symlink.
#
# See man:systemd-resolved.service(8) for details about the supported modes of
# operation for /etc/resolv.conf.

nameserver 127.0.0.53
options edns0
search hsd1.ca.comcast.net

---

