---
title: "Possible to DOWNGRADE Samba? Problems since upgrade. Asks for User/Pass to Win7 PC."
date: 2016-04-28
forum: General Help
---

### Post by 777funk on 2016-04-28
Is there a way to revert to my old version? I've broken my networking to my wife's machine. Can't print, can't access her files, etc. Been a real pain. 

I did an apt-get upgrade a couple days ago and boy was that a big mistake. 


I DO have a backup of my system but it's from when it was first installed. I only need would need that install of samba (nothing else). Is there a way to roll back?

---

### Post by 777funk on 2016-04-29
Anyone?

---

### Post by leunam12 on 2016-04-29
This will show you the different versions that are stored in your computer
```
sudo apt-cache showpkg <package name>
```
to install a previous version (you don't have to type the "<>"')
```
sudo apt-get install <packagename>=<version>
```

---

### Post by oldos2er on 2016-04-29
Please be patient. We have users from all over the world and it can take a day or more for everyone to see, let alone respond to, your post.

Also please provide some background information e.g. Ubuntu version, upgraded (?) from which version? Are you talking about a single package (samba) upgrade or ?

---

### Post by 777funk on 2016-04-29
Sorry about that! Sometimes not being able to print or reach needed files on the other computer on the network can feel like an emergency. I will shoot for 24 hours before pulling a thread back up. 

I will add a sig line shortly.

---

### Post by 777funk on 2016-04-29
sig line added

---

### Post by 777funk on 2016-04-29
Found my solution here:

[https://forums.linuxmint.com/viewtopic.php?f=157&p=1159792#p1159792](https://forums.linuxmint.com/viewtopic.php?f=157&p=1159792#p1159792)

Post #14-ish by xenopeek

```

sudo aptitude install samba-libs=2:4.1.6+dfsg-1ubuntu2  libsmbclient=2:4.1.6+dfsg-1ubuntu2 libwbclient0=2:4.1.6+dfsg-1ubuntu2  python-samba=2:4.1.6+dfsg-1ubuntu2 samba=2:4.1.6+dfsg-1ubuntu2  samba-common=2:4.1.6+dfsg-1ubuntu2  samba-common-bin=2:4.1.6+dfsg-1ubuntu2  samba-dsdb-modules=2:4.1.6+dfsg-1ubuntu2  samba-vfs-modules=2:4.1.6+dfsg-1ubuntu2 smbclient=2:4.1.6+dfsg-1ubuntu2  libldb1=1:1.1.16-1 python-ldb=1:1.1.16-1

```

---

### Post by 777funk on 2016-05-03
Well the problem is back... bummer.

---

