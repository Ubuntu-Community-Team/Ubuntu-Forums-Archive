---
title: "apt-cache policy libreoffice-calc"
date: 2014-08-20
forum: General Help
---

### Post by vasa1 on 2014-08-20
Can some who has the LibreOffice suite installed and fully updated, please run
```
apt-cache policy libreoffice-calc
``` and post the output here?

The reason I'm asking is that [I've put a "hold"]("http://ubuntuforums.org/showthread.php?t=2235031&p=13086449#post13086449") on the LibreOffice components I have and want to know how the "hold" is working.

This is what I'm seeing now:```
[11:13 AM] ~ $ apt-cache policy libreoffice-calc
libreoffice-calc:
  Installed: 1:4.2.4-0ubuntu2
  Candidate: 1:4.2.4-0ubuntu2
  Version table:
 *** 1:4.2.4-0ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
        500 http://archive.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages
        100 /var/lib/dpkg/status
     1:4.2.3~rc3-0ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
[11:13 AM] ~ $ 
```

---

### Post by Dennis N on 2014-08-20
In that command, candidate line will show the newer version if there is one found when you run apt-cache policy. 

Example:
```
dmn@Zotac:~$ apt-cache policy firefox
firefox:
  Installed: 30.0+build1-0ubuntu0.14.04.3
  Candidate: 31.0+build1-0ubuntu0.14.04.1
```

Here, firefox was pinned at 30.0

This was pinned in Synaptic. But, apt-get upgrade would install the newer firefox anyway:

```
dmn@Zotac:~$ apt-get -s upgrade
NOTE: This is only a simulation!
      apt-get needs root privileges for real execution.
      Keep also in mind that locking is deactivated,
      so don't depend on the relevance to the real current situation!
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  firefox firefox-locale-en
2 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

(Probably does not answer your question.)

---

### Post by vasa1 on 2014-08-20
> **Dennis N said:**
> In that command, candidate line will show the newer version if there is one found when you run apt-cache policy. 
...
(Probably does not answer your question.)
Well, it does a bit because my installed and candidate lines are the same. So maybe I'll need to wait some more to see what happens when an update (if any) is released before 14.10 is out.

BTW, I use apt-get via the CLI only. I don't use Synaptic or update manager. I check for updates with apt-get update and apt-get dist-upgrade at least twice a day.

---

### Post by vasa1 on 2014-09-02
I saw this today:```
Ign http://archive.ubuntu.com trusty/restricted Translation-en_IN
Ign http://archive.ubuntu.com trusty/universe Translation-en_IN
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  libreoffice-base-core libreoffice-calc libreoffice-common libreoffice-core
  libreoffice-gtk libreoffice-help-en-us libreoffice-style-galaxy
  libreoffice-style-human libreoffice-writer **python3-uno**
The following packages will be upgraded:
  chromium-codecs-ffmpeg-extra fonts-opensymbol gir1.2-gudev-1.0
  libgudev-1.0-0 libpam-systemd libsystemd-daemon0 libsystemd-login0 libudev1
  rsyslog systemd-services ubuntu-drivers-common udev uno-libs3 ure
  xserver-xorg-video-intel
15 upgraded, 0 newly installed, 0 to remove and 10 not upgraded.
Need to get 5,256 kB of archives.
After this operation, 130 kB disk space will be freed.
Do you want to continue? [Y/n] 
```
I continued and then ran apt-cache policy as before:```
[08:03 AM] ~ $ apt-cache policy libreoffice-calc
libreoffice-calc:
  Installed: 1:4.2.4-0ubuntu2
  Candidate: 1:4.2.6.3-0ubuntu1
  Version table:
     1:4.2.6.3-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
        500 http://archive.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages
 *** 1:4.2.4-0ubuntu2 0
        100 /var/lib/dpkg/status
     1:4.2.3~rc3-0ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
[08:03 AM] ~ $ 
```So, AFAICT, **hold** is doing its job probably because I'm using only apt-get update and apt-get dist-upgrade and not anything else. A minor point is that **python3-uno** is also held back even though it wasn't in my list. However, it seems to be totally to do with LibreOffice and nothing else, so not a problem.

---

