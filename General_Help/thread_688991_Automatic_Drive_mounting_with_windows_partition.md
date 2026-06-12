---
title: "Automatic Drive mounting with windows partition"
date: 2008-02-05
forum: General Help
---

### Post by herrshuster on 2008-02-05
Alright, here's my situation: I just got into ubuntu 7.10, wonderful, everything's peachy. I just installed windows xp (I need dreamweaver for work) and my hard drive is like this
hd0,0=linux
hd0,1=swap
hd0,2=windows
hd0,3=ntfs formatted partition for music, etc

in order for hd0,3 (BACKUP) to be mounted on the desktop or recognized by amarok (the music is on there), I have to go to places>system>backup, then enter my admin password. how can I avoid not doing that but still be able to access my data?:confused:

---

### Post by Gerard Barberi on 2008-02-05
For automatic mounting, you're looking to [edit fstab]("http://www.tuxfiles.org/linuxhelp/fstab.html")

It's located at /etc/fstab

---

### Post by FuturePilot on 2008-02-05
```
sudo apt-get install ntfs-config
```
Then go Applications&#8594;System Tools. Then you can configure access to NTFS drives/partitions. Then they should automatically get mounted when you login.

---

### Post by Gerard Barberi on 2008-02-06
> **herrshuster said:**
> Alright, here's my situation: I just got into ubuntu 7.10, wonderful, everything's peachy. I just installed windows xp (I need dreamweaver for work) and my hard drive is like this
hd0,0=linux
hd0,1=swap
hd0,2=windows
hd0,3=ntfs formatted partition for music, etc

in order for hd0,3 (BACKUP) to be mounted on the desktop or recognized by amarok (the music is on there), I have to go to places>system>backup, then enter my admin password. how can I avoid not doing that but still be able to access my data?:confused:

Sorry, I'm a little confused.  Are you trying to automatically mount it or mount it in a specific place?

---

### Post by herrshuster on 2008-02-06
you are both amazing. I installed ntfs-config, but it only worked for my windows install partition, then i used fstab and, based on how the other one was mounted i mounted the other one and it works perfectly. thank you so much!:KS

---

### Post by hyperair on 2008-02-06
Sounds like you need to configure your fstab right, as Gerard said earlier in post #2. You should also try using the Storage Device Manager (System->Administration->Storage Device Manager). If it isn't installed, then you have to install the "pysdm" package from Synaptic.

@Gerard: I believe herrshuster wants it automatically mounted.

---

