---
title: "Can't install Mplayer - Unmet dependencies"
date: 2014-01-13
forum: General Help
---

### Post by james-auble2 on 2014-01-13
I can't seem to install mplayer or mplayer2. 

Installing mplayer2 with apt-get I get this:
```
james@james-X45C:~$ sudo apt-get install mplayer2Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libvdpau1
Suggested packages:
  nvidia-vdpau-driver vdpau-driver
The following NEW packages will be installed:
  libvdpau1 mplayer2
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,195 kB of archives.
After this operation, 3,124 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ saucy/main libvdpau1 amd64 0.7-1 [30.3 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ saucy/universe mplayer2 amd64 2.0-554-gf63dbad-1ubuntu1 [1,164 kB]
Fetched 1,195 kB in 7s (152 kB/s)                              
(Reading database ... 214434 files and directories currently installed.)
Unpacking libvdpau1:amd64 (from .../libvdpau1_0.7-1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libvdpau1_0.7-1_amd64.deb (--unpack):
 trying to overwrite shared '/etc/vdpau_wrapper.cfg', which is different from other instances of package libvdpau1:amd64
Selecting previously unselected package mplayer2.
Unpacking mplayer2 (from .../mplayer2_2.0-554-gf63dbad-1ubuntu1_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for mime-support ...
Errors were encountered while processing:
 /var/cache/apt/archives/libvdpau1_0.7-1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
james@james-X45C:~$ 



```

I tried running 'sudo apt-get install -f' to fix, but I get: 

```
james@james-X45C:~$ sudo apt-get install -fReading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libvdpau1
Suggested packages:
  nvidia-vdpau-driver vdpau-driver
The following NEW packages will be installed:
  libvdpau1
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0 B/30.3 kB of archives.
After this operation, 115 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 214440 files and directories currently installed.)
Unpacking libvdpau1:amd64 (from .../libvdpau1_0.7-1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libvdpau1_0.7-1_amd64.deb (--unpack):
 trying to overwrite shared '/etc/vdpau_wrapper.cfg', which is different from other instances of package libvdpau1:amd64
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 /var/cache/apt/archives/libvdpau1_0.7-1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
james@james-X45C:~$ 



```

On the advise of posts I tried removing some of the ppas i've added but that didn't have an effect. 

How should I proceed to fix this?

---

### Post by mc4man on 2014-01-13
Either purge libvdpau1 if it's installed, then update sources & re-install 
or
Just  remove /etc/vdpau_wrapper.cfg, then install libvdpau1, ect.

---

### Post by james-auble2 on 2014-01-13
Removing /etc/vdpau_wrapper.cfg and installing libvdpau1 worked. 

Thanks!

---

