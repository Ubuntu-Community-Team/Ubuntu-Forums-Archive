---
title: "can't install kate"
date: 2019-06-25
forum: General Help
---

### Post by ReneVeerman on 2019-06-25
```
root@crow:/home/rene/Desktop/__README__INSTALLATION_INSTRUCTIONS# apt --fix-broken install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following additional packages will be installed:
  libqt5quick5
The following NEW packages will be installed:
  libqt5quick5
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
142 not fully installed or removed.
Need to get 0 B/1201 kB of archives.
After this operation, 4905 kB of additional disk space will be used.
Do you want to continue? [Y/n] 
(Reading database ... 185028 files and directories currently installed.)
Preparing to unpack .../libqt5quick5_5.9.5-0ubuntu1.1_amd64.deb ...
Unpacking libqt5quick5:amd64 (5.9.5-0ubuntu1.1) ...
dpkg-deb (subprocess): decompressing archive member: lzma error: compressed data is corrupt
dpkg-deb: error: <decompress> subprocess returned error exit status 2
dpkg: error processing archive /var/cache/apt/archives/libqt5quick5_5.9.5-0ubuntu1.1_amd64.deb (--unpack):
 cannot copy extracted data for './usr/lib/x86_64-linux-gnu/libQt5Quick.so.5.9.5' to '/usr/lib/x86_64-linux-gnu/libQt5Quick.so.5.9.5.dpkg-new': unexpected end of file or stream
Errors were encountered while processing:
 /var/cache/apt/archives/libqt5quick5_5.9.5-0ubuntu1.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@crow:/home/rene/Desktop/__README__INSTALLATION_INSTRUCTIONS# 

```
eh... i'm stuck. :(
this is happening on a fresh install of ubuntu 18.04, which had no problems installing a full apache stack and video card drivers, etc.

---

### Post by ReneVeerman on 2019-06-25
first i used apt-get auto-remove and apt-get clean

then i did a reboot of the machine, followe by a 
sudo rm /var//lib/apt/lists/*

and then a sudo apt update

and a final sudo apt install kate

succeeded.

strange error, and i don't know if i can trust my disks this way.

but we'll see, it's not mission-critical stuff anyways.

---

### Post by CatKiller on 2019-06-25
> **ReneVeerman said:**
> strange error, and i don't know if i can trust my disks this way.

It wasn't necessarily a disk error; it could have just been a corrupted download because of transient internet conditions. That's why the files include checksums, after all. Glad you got it sorted.

---

