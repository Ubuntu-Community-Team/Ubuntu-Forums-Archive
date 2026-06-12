---
title: "Disk Partioning General Theory"
date: 2007-12-22
forum: General Help
---

### Post by cubical10 on 2007-12-22
Hello;

I installed 7.10 Desktop using most of the default options erasing the entire disk for a fresh install as this is my first look at Ubuntu (which I like :)).
From my past experience with Linux and Solaris, disk partitioning  usually involved mounting /tmp on its own partition of type tmpfs or swap.  After my install I see this is not the case for Ubuntu 7.10.

```
$ df -ahT
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda1     ext3     72G   19G   50G  28% /
proc          proc       0     0     0   -  /proc
/sys         sysfs       0     0     0   -  /sys
varrun       tmpfs    756M  216K  755M   1% /var/run
varlock      tmpfs    756M     0  756M   0% /var/lock
udev         tmpfs    756M   64K  756M   1% /dev
devshm       tmpfs    756M     0  756M   0% /dev/shm
devpts      devpts       0     0     0   -  /dev/pts
lrm          tmpfs    756M   34M  722M   5% /lib/modules/2.6.22-14-generic/volatile
securityfs
        securityfs       0     0     0   -  /sys/kernel/security
$
```

I am curious as to why this is not part of the standard partitioning scheme for Ubuntu?  I only ask as its what I am used to seeing.

Is it worth the effort to repartition, pulling 1G out of / and creating a /tmp partition?
This is my multipurpose home server/dev station/ whatever machine.
Top services/apps I use are: samba, LAMP stack and Eclipse IDE.

---

### Post by p_quarles on 2007-12-22
I'm afraid I don't have a lot of experience with Solaris, and haven't used any Linux distros that have asked for a separate /tmp partition. Still, I might be able to answer your question if you can explain the purpose of a separate partition for this part of the filesystem. I plead ignorance. ;) It is, of course, very easy to set up, but I can't think of a reason to do so.

FYI, Ubuntu *does* have a separate swap partition, but it won't show up in df output. To see your swap, you can use either of these:
```
sudo fdisk -l
```
or
```
free
```
For a web and SMB server, it might make sense to allocate separate partitions for /home and /var -- these could make it simpler to reinstall the base system without losing data.

---

### Post by wub on 2007-12-26
I do not know theory, but I can give an example:

Good news:

Many, many moons ago (RH 5.1) I installed an SQL database server (Interbase 4.0).  I had set up my system with distinct /tmp and /var partitions, following advice from a book.  The main system logs go into /var/log, and when a Windows client unexpectedly stopped responding to Interbase (read: crash), the server would mention this in the system log.  Unfortunately, there was a bug in the logging logic, and even on old, slow hardware, it was writing over 300 messages per minute.  Many folks would see their hard drive fill up every few days, causing their system to go catatonic.  My partition would fill up, but my server stayed responsive, since the rest of the disk was safe.

Bad news:

On occasion, I would have serious trouble installing packages from source since they would default to using /tmp, and my particular partition limit was too small for their purpose.

---

