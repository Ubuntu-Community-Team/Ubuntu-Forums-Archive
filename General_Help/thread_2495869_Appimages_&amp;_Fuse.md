---
title: "Appimages &amp; Fuse"
date: 2024-03-05
forum: General Help
---

### Post by tqtim on 2024-03-05
Using 22.04.4 LTS

Yesterday I tried to run Electrum appimage and Trezor Suite appimage and neither would run. Bit of interwebbing and it look like an upgrade has broken things!

Using the terminal I get the message;

User:~/Downloads/Set Ups/Electrum Latest$ ./electrum-4.5.3-x86_64.AppImage
dlopen(): error loading libfuse.so.2

AppImages require FUSE to run. 
You might still be able to extract the contents of this AppImage 
if you run it with the --appimage-extract option. 
See [https://github.com/AppImage/AppImageKit/wiki/FUSE](https://github.com/AppImage/AppImageKit/wiki/FUSE) 
for more information

The github page says 'Warning: While libfuse2 is OK, do not install the fuse package as of 22.04 or you may break your system'. 

I checked for FUSE using;
User:~/Desktop$ dpkg -l | grep fuse3
ii  fuse3                                      3.10.5-1build1                          amd64        Filesystem in Userspace (3.x version)
ii  libfuse3-3:amd64                           3.10.5-1build1                          amd64        Filesystem in Userspace (library) (3.x version)

So, I do have FUSE3?

Firstly, I don't want to break my system and I'm led to believe that if I install Fuse alongside my existing FUSE I 'have to accept the consequences'!!

All seems a complete C**k up to me, it wasn't broke but someone fixed it.

Do I proceed with the instructions from [https://docs.appimage.org/user-guide/troubleshooting/fuse.html#setting-up-fuse-2-x-alongside-of-fuse-3-x-on-recent-ubuntu-22-04-debian-and-their-derivatives](https://docs.appimage.org/user-guide/troubleshooting/fuse.html#setting-up-fuse-2-x-alongside-of-fuse-3-x-on-recent-ubuntu-22-04-debian-and-their-derivatives)

Instructions are to use
> sudo apt install libfuse2

Noting that github says don't install FUSE if you have 22.04 which is what I've got. Who'd imagine you'd find conflicting interweb info!

Or is it 50/50 as to 'will everything work as it did before someone fiddled' or is that the end of appimages for me with a broke system :(

Thanks
Tim

---

### Post by ActionParsnip on 2024-03-05
What is the output o:
```

sudo updatedb
locate [COLOR=#E8E6E3]libfuse*

```
Thanks[/COLOR]

---

### Post by Dennis N on 2024-03-05
Based on my experience, installing libfuse2 does not cause a problem. My Ubuntu 22.04 system has both libfuse2 and libfuse3 installed:

```
dmn@Sydney:~$ dpkg --list libfuse*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name             Version        Architecture Description
+++-================-==============-============-===============================================
ii  libfuse2:amd64   2.9.9-5ubuntu3 amd64        Filesystem in Userspace (library)
ii  libfuse3-3:amd64 3.10.5-1build1 amd64        Filesystem in Userspace (library) (3.x version)
```

---

### Post by tqtim on 2024-03-05
Actionparsnip

Out from that code is 'command not found'.

Is there a typo?
Thanks though.
Tim

---

