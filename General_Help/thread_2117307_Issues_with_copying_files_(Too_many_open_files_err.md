---
title: "Issues with copying files (Too many open files error along with high CPU and memory)"
date: 2013-02-18
forum: General Help
---

### Post by xternal7 on 2013-02-18
Hi. I'm trying to copy a fair amount of files from one drive to another (NTFS to NTFS) and during copying I always encounter:
— High CPU usage
— Memory usage going way out of hand 
— (when copying over USB, also often also slower transfer speeds than I was accustomed to in Windows)

In addition to that, my laptop tends to freeze fairly often due to 'Too many open files' error. (Plasma-desktop crashes, programs stop responding and TTY sessions stop accepting commands). 

What I was/am doing: 
Copying ~60k files (~70 GB) to samba drive.
Copying ~120k files (~265 GB) to external HDD.

---

### Post by dino99 on 2013-02-18
if you select too much files at once, then be sure to have enough ram room and a wide swap partition  , otherwise you get  what you have seen. Better to use windows as you are moving files from ntfs to ntfs (instead of linux which need to use one more driver (ntfs-3g) )

---

### Post by rnerwein on 2013-02-18
> **xternal7 said:**
> Hi. I'm trying to copy a fair amount of files from one drive to another (NTFS to NTFS) and during copying I always encounter:
&#8212; High CPU usage
&#8212; Memory usage going way out of hand 
&#8212; (when copying over USB, also often also slower transfer speeds than I was accustomed to in Windows)

In addition to that, my laptop tends to freeze fairly often due to 'Too many open files' error. (Plasma-desktop crashes, programs stop responding and TTY sessions stop accepting commands). 

What I was/am doing: 
Copying ~60k files (~70 GB) to samba drive.
Copying ~120k files (~265 GB) to external HDD.
hi
if you ain't something in /etc/security/limits.conf i guess you have a run-away process (here fd-runaway - process just open a file and forget to close it). the fd-limit is normaly set to unlimited [ i always change this ].
when your copy is running:
1. open a terminal
2. sudo -i
3. lsof > bla
4. wait 2 or 3 minutes
5. lsof > blu
6. sort bla > bla1
7. sort blu > blu1
8. diff bla1 blu1 | more
now you can easy see whick process have the rising fds.
oh yes: copying a huge amount of files is cpu and memory intesive. but for memory look with "top" on your cache-size !
which command you use to copy the files ?
ciao

---

### Post by xternal7 on 2013-02-19
> **dino99 said:**
> if you select too much files at once, then be sure to have enough ram room and a wide swap partition  , otherwise you get  what you have seen. Better to use windows as you are moving files from ntfs to ntfs (instead of linux which need to use one more driver (ntfs-3g) )

RAM and SWAP are sufficient, I've usually still got about 2G of SWAP left when thing crashes.

> **rnerwein said:**
> 
which command you use to copy the files ?


I do it via GUI.

---

### Post by rnerwein on 2013-02-25
> **xternal7 said:**
> RAM and SWAP are sufficient, I've usually still got about 2G of SWAP left when thing crashes.



I do it via GUI.
hi
i told you it is not RAM or SWAP. the system is run out of FD's.
have you tried the "lsof" ??? to see who is using up all of your FD's.
ciao

---

### Post by xternal7 on 2013-02-25
> **rnerwein said:**
> hi
i told you it is not RAM or SWAP. the system is run out of FD's.
have you tried the "lsof" ??? to see who is using up all of your FD's.
ciao

The RAM/SWAP line was meant for the other commenter.

I tried lsof, but I didn't figure much out of it. I ended up copying everything in TTY2 session via cp command and I didn't get these problems anymore.

---

### Post by Gyokuro on 2013-02-25
Hi

The problem is with nautilus/gvfs and it is an old problem - sorry do not be more helpful in this case but it is better as you have already done to copy large amounts of data via cp or you can even copy a lot of files with rsync (rsync has nice features in case your connection timed out).  Sometimes I have to copy hundreds of GB via rsync.

---

