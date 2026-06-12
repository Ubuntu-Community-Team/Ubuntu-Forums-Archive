---
title: "Ubuntu Freenx - install issue on dapper 6.06"
date: 2007-01-28
forum: General Help
---

### Post by grekoo on 2007-01-28
I am trying to install freenx server on an ubuntu 6.06 box i say try but i don't know what i have done wrong i have to admit i haven't been using linux that long this is what i have done so far:o 

```
I added the following to the /etc/apt/sources.list file:-

deb http://free.linux.hp.com/~brett/seveas/freenx dapper-seveas freenx
deb-src http://free.linux.hp.com/~brett/seveas/freenx dapper-seveas freenx

then i authenticated the packages by using the following:-

# wget http://free.linux.hp.com/~brett/seveas/freenx/1135D466.gpg -O- | sudo apt-key add -

# wget http://seveas.theplayboymansion.net/seveas/1135D466.gpg -O- | sudo apt-key add -

Then i fixed the dependency issue:-

# wget http://mirrors.kernel.org/ubuntu/pool/universe/g/gcc-2.95/libstdc++2.10-glibc2.2_2.95.4-24_i386.deb

# sudo dpkg -i libstdc++2.10-glibc2.2_2.95.4-24_i386.deb

Then i updated the install list

# apt-get update

and then i installed the freenx software:-

#  sudo apt-get install ssh freenx nxclient libxcomp1 libxcompext1 nxagent nxdesktop nxviewer

Debconf started up and asked what type of key i want to use i left the config alone

```

I then installed the client software on my xp box imported the key from the ubuntu server to my Windows Xp box and when i try to logon i recieve the following error when i click on details to view the error 

> NX> 1000 NXNODE - Version 1.4.0-45-SVN OS (GPL)
NX> 700 Session id: peter-desktop-1002-0F2F37E98DC3E33A71C12D940AEC3988
NX> 705 Session display: 1002
NX> 703 Session type: unix-gnome
NX> 701 Proxy cookie: 8bc2c1c482babc821e9966655143dc7a
NX> 702 Proxy IP: 127.0.0.1
NX> 706 Agent cookie: 63a9f0ea7bb98050796b649e85481845
NX> 704 Session cache: unix-gnome
NX> 707 SSL tunneling: 1
/usr/lib/nx/nxserver: line 891:  6940 Terminated              ( sleep $AGENT_STARTUP_TIMEOUT; exit 1 )
NX> 105 NX> 504 Session startup failed.
NX> 1004 Error: nxagent failed to start with: Unrecognized option: 1
NX> 1001 Bye.
Killed by signal 15.

I hope someone can help me with this as i would really love to get this software working as i have been told that it works better than VNC.

Thanks:KS :KS

---

### Post by grekoo on 2007-01-28
Very strange just tried nxclient on the nxserver freenx ubuntu box and i can establish a connection fine   - i can also establish a ssh sesion via putty from my xp box.

Thanks hope someone can help with this :D

---

### Post by rvergara on 2007-01-28
Hi,

I have exactly the same problem.

The funny thing is that I had a working connection (Ubuntu 6.06, remore client on XP, NX client version 1.5) until I lost the HD in my XP laptop so I had to download a new NX client, I have been unable to connect to my Ubuntu 6.0.6 since then. I assume the problem is related to the NX windows client and not with Ubuntu (at least this is what I have thought). NX client 1.5 used to work, but newer 2.x clients do not.

Any ideas in the forum on what to do?, i have been googling to see if I can download 1.5 from somewhere to no avail.

Any ideas are welcome.

Thanks

Ramiro

---

### Post by nsilva on 2007-03-25
I'm having the same problem, running Ubuntu 6 Server with an XP NxClient 2.1

---

### Post by nsilva on 2007-03-25
> **rvergara said:**
> Hi,

I have exactly the same problem.

The funny thing is that I had a working connection (Ubuntu 6.06, remore client on XP, NX client version 1.5) until I lost the HD in my XP laptop so I had to download a new NX client, I have been unable to connect to my Ubuntu 6.0.6 since then. I assume the problem is related to the NX windows client and not with Ubuntu (at least this is what I have thought). NX client 1.5 used to work, but newer 2.x clients do not.

Any ideas in the forum on what to do?, i have been googling to see if I can download 1.5 from somewhere to no avail.

Any ideas are welcome.

Thanks

Ramiro
Ramiro was right the problem was with the Windows built.
It got it working with version 1.5

to find 1.5 versions: [http://www.industrial-statistics.com/info/nxclients](http://www.industrial-statistics.com/info/nxclients)

---

### Post by rvergara on 2007-06-04
Nsilva,

Thanks for the link.

I reinstall nxclient 1.5 and now I can connect to the Ubuntu box again.

Regards

Ramiro

---

