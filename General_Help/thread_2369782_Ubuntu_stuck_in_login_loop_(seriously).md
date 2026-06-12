---
title: "Ubuntu stuck in login loop (seriously)"
date: 2017-08-26
forum: General Help
---

### Post by someoe on 2017-08-26
I found alot of questions with the same title put it all can't help.

My os : Ubuntu 16.04 LTS amd64 (xenial)

My kernel : 4.12.0-041200 kernel

My ~/.xsession-errors :

openConnection: connect: No such file or directory
cannot connect to brltty at :0
upstart: gnome-session (GNOME) main process (1603) terminated with status 1
upstart: logrotate main process (1449) killed by TERM signal
upstart: update-notifier-crash (/var/crash/libglapi-mesa.0.crash) main process (1504) killed by TERM signal
upstart: update-notifier-crash (/var/crash/libsdl2-2.0-0.0.crash) main process (1505) killed by TERM signal
upstart: update-notifier-crash (/var/crash/libvdpau1.0.crash) main process (1506) killed by TERM signal
upstart: bamfdaemon main process (1556) killed by TERM signal
upstart: Disconnected from notified D-Bus bus
and All my pakages is upgraded

Please help me with this

I have tried to replace libglapi-mesa new verion with an old one, and the package dependencies did't match with the package version and i have removed sources.list file and removed the main packages then followed this Cannot boot system due to start job running for hold then this problem happend

and i have another question :

What is the default ubuntu 16.04.3 lts kernel?

---

### Post by jeremy31 on 2017-08-26
*Thread moved to **General Help**.*

---

### Post by Bashing-om on 2017-08-26
someoe; Ouch !

> 
 i have removed sources.list file and removed the main packages


Show us what is now/
Post back - between code tags - the outputs of terminal commands:
```

cat /etc/apt/sources.list
sudo apt update
sudo apt upgrade
sudo apt -f install
ls -al .ICEauthority .Xauthority
sudo lshw -C display

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

See from this what we have and where to go from here.

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

