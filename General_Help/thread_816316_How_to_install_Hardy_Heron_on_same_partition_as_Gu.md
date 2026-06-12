---
title: "How to install Hardy Heron on same partition as Gutsy and thus erase the Latter?"
date: 2008-06-02
forum: General Help
---

### Post by psychedelix on 2008-06-02
I want to install Hardy Heron.  But I do not want to keep my Gutsy; I want to install Hardy on same partition as Gutsy was initially.  Can somebody help me out?  Coz on the installation cd, when I launch it, when I come to partition, the Hardy seems to want to co-exist with Gutsy.  And this I do not want.  Can somebody help me plz?

P.S : I am linux newbie.

Thank you from the bottom of my heart.

---

### Post by bingoUV on 2008-06-02
Post the output of the following command from a terminal. Applications -> Accessories -> Terminal

```

mount

```

This command does not make any change to your system. It will just let us know of the status of your OS installation with regard to partitions.

---

### Post by psychedelix on 2008-06-02
I am pasting the output:
/dev/sda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)

Now how do I proceed with the installation?

---

### Post by bingoUV on 2008-06-02
Choose "manual" partition method. Now, select /dev/sda3  , with mount point /. Don't select any other partition device on the manual partition screen. Check the format option.

Note that this will remove all your data from your earlier installation. Report back if some option is not exactly as I mentioned above. You can access internet/this forum while installing.

---

### Post by abn91c on 2008-06-02
if you don want to save any files select use entire disk option if doing a fresh install

---

