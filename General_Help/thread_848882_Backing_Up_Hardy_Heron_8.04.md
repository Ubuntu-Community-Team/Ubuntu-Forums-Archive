---
title: "Backing Up Hardy Heron 8.04?"
date: 2008-07-03
forum: General Help
---

### Post by Syndicated on 2008-07-03
Hi,

I finally was able to get Hardy Heron 8.04 all setup and ready to go. Now my questions is what commands or programs could I use to back up all my settings and or installation of everything? I was planning on using either a dual layer dvd for back up or an external hard drive. Any help would be appreciated.


-Syndicated

---

### Post by mike2357 on 2008-07-04
There are lots of different programs you can use to back up files.  I personally use "zip", because it can be used in both the Linux and Windows worlds.  Other possibilities are "tar" and "cpio".

I have cron set up to run a daily backup of everything in /home, /etc and /var/spool/cron/crontabs, and every few days I move the backup file to another computer.  I've done more than my share of trashing settings in /etc, and I've been saved more than once by having a backup.

---

### Post by smo0th on 2008-07-04
you can make a complete backup with 

```
tar cvpjf backup.tar.bz2 --exclude=/proc --exclude=/lost+found --exclude=/backup.tar.bz2 --exclude=/mnt --exclude=/sys /

```
and recover your backup with

```
tar xvpfj backup.tar.bz2 -C /
```

but don't forget to create the directories you exclude like

```
mkdir /mnt
```

or whatever you need, you can use the same for any directory/partition instead the root.

---

