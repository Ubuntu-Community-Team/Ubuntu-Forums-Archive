---
title: "kernel panic on triple boot ubuntu"
date: 2007-01-21
forum: General Help
---

### Post by ndrw on 2007-01-21
my dapper ubuntu will not boot any more.

the error it gives is this:
KERNEL PANIC - NOT SYNCING: VFS UNABLE TO MOUNT ROOT FS ON UNKNOWN BLOCK (8,3)

the last thing I did was a software update.

I am running it on a partitioned triple boot macbook pro.

the rescue mode hangs when I try to do anything.

ideas?

---

### Post by dcstar on 2007-01-21
> **ndrw said:**
> my dapper ubuntu will not boot any more.

the error it gives is this:
KERNEL PANIC - NOT SYNCING: VFS UNABLE TO MOUNT ROOT FS ON UNKNOWN BLOCK (8,3)

the last thing I did was a software update.

I am running it on a partitioned triple boot macbook pro.

the rescue mode hangs when I try to do anything.

ideas?

Boot off the Live CD and do a fsck on your Linux partition.

---

### Post by ruicovelo on 2007-02-13
That happened to me too. If anyone gets around this, please let us know :)

---

### Post by energiya on 2007-02-13
> **ndrw said:**
> my dapper ubuntu will not boot any more.

the error it gives is this:
KERNEL PANIC - NOT SYNCING: VFS UNABLE TO MOUNT ROOT FS ON UNKNOWN BLOCK (8,3)

the last thing I did was a software update.

I am running it on a partitioned triple boot macbook pro.

the rescue mode hangs when I try to do anything.

ideas?

The same thing happened to me after compiling the kernel and marked <M> my XFS file system. This is probably a stupid question, but did the software you updated had any connection with the kernel or other critical modules?

---

### Post by ruicovelo on 2007-02-13
To be true, I don't really know what I updated. I just hit "update" :(

Is there any log of the last updates?

---

### Post by igknighted on 2007-02-13
If I remember correctly that error message has to do with grub not properly telling your system where the root partition is.  Can you post your /boot/grub/menu.lst file please?
```
cat /boot/grub/menu.lst
```

---

### Post by ruicovelo on 2007-02-13
Well... I'm using lilo and lilo.conf is exactly as it was before the updates. :(

---

### Post by Spemi on 2007-04-20
I have the exact same problem. I installed Ubuntu 6.10 edgy a few months ago on a triple boot macbook pro. It took me a couple of days before I got it all working and then I left Ubuntu alone for a while. Yesterday I configured my audio and video drivers, installed automatix2 and did some updates with update manager. Since then I can't reboot, allways get the error mentioned above. Can anyone help me, I'm a complete linux noob and need very detailed instructions.

Thx

---

### Post by ruicovelo on 2007-04-20
I accepted defeat :)

I wanted to try the new Ubuntu 7.04 (beta) so I reinstalled Ubuntu with the new version from CD. It's working for now...

---

### Post by moktin on 2007-04-22
Hello, 
I'm also on Mac Book and it's the third time I have this problem in two weeks...
The two first time I accepted the defeat, but today, I really don't want... I've got a really bad internet connection and have a quiet heavy environment to install... So this time I don't want to reinstall all.
My configuration is :
Macbook core duo on kubuntu with refit and lilo as bootloader
The first time it happend I trie to upgrade to the beta fiesty
The second time I just do the normal upgrade
The third time I upgrade to fiesty

I ever tried to try booting with older kernel, but have the same problem.
And when I mount my partition manually with the live CD, chroot to it and try :
> #lilo
I have this error :
fatal: raid_setup: stat("/dev/sda3")

fsck encountered no problems
I really hope you can help me.

---

### Post by superfluous_nut on 2007-05-09
i had the same issue -- edgy install that updated to feisty.  everything updated, rebooted and panic.  macbook triple booting using refit.

i fixed it by booting from edgy install disk and doing this:

sudo su -

parted /dev/sda
set 3
boot
on
quit

mkdir /mnt/ubuntu
mount /dev/sda3 /mnt/ubuntu
mount -t proc none /mnt/ubuntu/proc
mount -o bind /dev /mnt/ubuntu/dev
chroot /mnt/ubuntu /bin/bash

lilo -P fix


you might recognize that sequence from the triple boot mac faq that's floating around.

i'm not sure the parted bit is necessary, but i did it and my set up works.

after you do all that stuff, reboot and go to refit's partition tool and resync the mbr/gpt stuff.  reboot to linux.  if it hangs at the penguin, then reboot to os x or windows and see if that fixes things.  it did for me.

good luck.


in hindsight, after updating the kernel, you could probably just do a simple "lilo -P fix" to ensure that the boot params are reset as that's really all that going on above.  all the other stuff is just prefacing the lilo -P fix command to set things up so lilo knows what to do.

---

