---
title: "FreeNX quits after authentication"
date: 2005-10-28
forum: General Help
---

### Post by matw on 2005-10-28
I installed FreeNX in Breezy, but when I try to connect using a Win client, the server quits. In ~/.nx/C-1006.../session, there are a bunch of messages about connection established, using fast copy area mode in agent, ..., and then there's this
```

X Error: BadwWindow
  Request Magor code 2 ()
  ResourceID 0x7461d2f
  Error Serial #38

gnome-session: Fatal IO error 104 (Connection reset by peer) on X server unix:1006.0.

```

On the client side I get a window with an X cursor and a !M logo on a black backgound. After a while a dialog pops up and tells me the server isn't responding.

Any ideas?

---

### Post by matw on 2005-10-29
This is a bug. I built FreeNX from from source packages from the breezy-seveas repository on AMD64 ubuntu. I reinstalled i386 ubuntu, and then installed the FreeNX binaries, which worked perfectly.

---

### Post by RSX311 on 2005-10-31
[QUOTE=matw]This is a bug. I built FreeNX from from source packages from the breezy-seveas repository on AMD64 ubuntu. I reinstalled i386 ubuntu, and then installed the FreeNX binaries, which worked perfectly.[/QUOTE]

how do you know it's a bug? I think I have the same problem.  It authenticates and tries to show the display and it sits there and does nothing showing the NX logo.

---

### Post by nyssa on 2005-11-01
Hi,

i have the same problem.

Ubuntu Breezy AMD64, NX stuff rebuild for amd64 from breezy-seveas.

Shows NX logo then nothing, found a core file in users home and this in syslog...

nxagent[28496]: segfault at ffffffffffffffe4 rip 00002aaaab3eb0b7 rsp 00007fffffcb5000 error 6

:(

---

### Post by TitoPuente on 2005-11-21
Hi all,

Same for me. Nxagent generates a kernel error with sources   compiled under Breezy with an AMD64 .

Message from syslog ( /var/log/ ):

kernel: [12113.657307] nxagent[20889]: segfault at ffffffffffffffe4
 rip 00002aaaab3e40b7 rsp 00007fffffd78750 error 6

Sources were from:

deb-src [http://seveas.ubuntulinux.nl/](http://seveas.ubuntulinux.nl/) breezy-seveas freenx

I am a bit disapointed. I have spent the entire day on that issue. Anyway...I will log a bug on the freenx website.

:(

---

### Post by saitta on 2006-03-19
[QUOTE=TitoPuente]Hi all,

Same for me. Nxagent generates a kernel error with sources   compiled under Breezy with an AMD64 .

Message from syslog ( /var/log/ ):

kernel: [12113.657307] nxagent[20889]: segfault at ffffffffffffffe4
 rip 00002aaaab3e40b7 rsp 00007fffffd78750 error 6

Sources were from:

deb-src [http://seveas.ubuntulinux.nl/](http://seveas.ubuntulinux.nl/) breezy-seveas freenx

I am a bit disapointed. I have spent the entire day on that issue. Anyway...I will log a bug on the freenx website.

:([/QUOTE]

Hi ,

Just to get it running on an AMD64 I built the packages both for AMD64 and i386.
Installed the AMD64 version and replaced the nxagent binary with the 32 bit version.
I copied the required 32 bit libs to /usr/lib32
Following libs needed to be copied on my system:
libX11-nx.so.6
libXcompext.so.1
libXcomp.so.1
libXext-nx.so.6
libXrender-nx.so.1

That allows FreeNX server to run on my AMD64 box.

:-D

---

### Post by countryboy on 2006-05-02
[QUOTE=saitta]Hi ,

Just to get it running on an AMD64 I built the packages both for AMD64 and i386.
Installed the AMD64 version and replaced the nxagent binary with the 32 bit version.
I copied the required 32 bit libs to /usr/lib32
Following libs needed to be copied on my system:
libX11-nx.so.6
libXcompext.so.1
libXcomp.so.1
libXext-nx.so.6
libXrender-nx.so.1

That allows FreeNX server to run on my AMD64 box.

:-D[/QUOTE]

Sorry Saitta, could you be a little more explicit in what you did? I am trying also to run FreeNX on an AMD64 installation of Breezy.

Thanks

---

### Post by countryboy on 2006-05-02
[QUOTE=saitta]Hi ,

Just to get it running on an AMD64 I built the packages both for AMD64 and i386.
Installed the AMD64 version and replaced the nxagent binary with the 32 bit version.
I copied the required 32 bit libs to /usr/lib32
Following libs needed to be copied on my system:
libX11-nx.so.6
libXcompext.so.1
libXcomp.so.1
libXext-nx.so.6
libXrender-nx.so.1

That allows FreeNX server to run on my AMD64 box.

:-D[/QUOTE]

Ok, I followed what you wrote above:
- installed FreeNX
- copied all the above files from a 32 bit version to my AMD64 machine

No luck. It crashes soon after authentication. this is the log from my client:

NX> 1000 NXNODE - Version 1.4.0-45-SVN OS (GPL)
NX> 700 Session id: dexter-arm-1000-A308A97CBC959A8E84C68070C79E80BB
NX> 705 Session display: 1000
NX> 703 Session type: unix-gnome
NX> 701 Proxy cookie: d76ea68659b5971c9be92626dd01d952
NX> 702 Proxy IP: 130.155.72.67
NX> 706 Agent cookie: d76ea68659b5971c9be92626dd01d952
NX> 704 Session cache: unix-gnome
NX> 707 SSL tunneling: 0
NX> 1004 Error: Session did not start.
NX> 504 Session startup failed.
NX> 999 Bye
Killed by signal 15.

---

### Post by filiep on 2006-05-05
I also managed running it on my AMD64 box.
Just als Saitta told, I compiled the stuff on a i386 box and copied the nxagent and the library files over. But be aware that the mentioned library files are symbolic links, so you have to copy over the files to which the symlinks points aswell.

F.

---

