---
title: "Reiser4 filesystem"
date: 2005-03-28
forum: General Help
---

### Post by DougZ on 2005-03-28
Not quite sure where to post this...

Installed the reiser4 progs (can't remember from which repository) and I can create a resier4 fs no problem on a partition.  But I can't mount it!!! I get an error claiming unknown filesystem type, or something like that.

Am I missing something?

---

### Post by localzuk on 2005-03-28
Have you tried mounting it using mount -t reiserfs /dev/hdxX /wherever/you/want/it, also do you have reiserfs support in your kernel? (Not sure if it included by default - though it should be).

---

### Post by DougZ on 2005-03-28
It is the creation that is actually failing I think, judging by the errors I get.

I created the fs with "mkfs.reiser4 /dev/hdc1":

mkfs.reiser4 1.0.3
Copyright (C) 2001, 2002, 2003, 2004 by Hans Reiser, licensing governed by
reiser4progs/COPYING.

Block size 4096 will be used.
Linux 2.6.10-5-386 is detected.
Uuid 705f76ea-d5bd-4893-bb7e-7c3e1a2417ee will be used.
Reiser4 is going to be created on /dev/hdc1.
(Yes/No): Yes
Creating reiser4 on /dev/hdc1 ... done

...And tried to mount it with "mount -t reiserfs /dev/hdc1 /mnt/hdc1"

mount: wrong fs type, bad option, bad superblock on /dev/hdc1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

and if I run "reiserfsck /dev/hdc1" I get:

reiserfs_open: the reiserfs superblock cannot be found on /dev/hdc1.
Failed to open the filesystem.

If the partition table has not been changed, and the partition is
valid  and  it really  contains  a reiserfs  partition,  then the
superblock  is corrupted and you need to run this utility with
--rebuild-sb.

It's not a high-piority thing, just something I wanted to mess around with.  So I'm going to back-burner this and try again another day.

---

### Post by mimek on 2005-03-29
Hi,

You are using wrong tools.

Reiser4 is a new filesystem and as far as I know it isn't in the kernel yet (I had to recompile kernel with reiser4 paches) an because of that you cannot mount it.

To check reisr4 fs use fsck.reiser4 an it'll be ok, but as i wrote you have to ensure that your kernel supports   reiser4.

---

### Post by DougZ on 2005-04-11
Mind sharing which patches you used?

I've tried several combinations of patches with no success. I cannot get ubuntu's "flavour" of the 2.6.10 kernel to compile cleanly with reiser4 patched in.

---

### Post by mimek on 2005-04-15
[QUOTE=DougZ]Mind sharing which patches you used?[/QUOTE]

At the moment I'm using an original linux 2.6.11 kernel with cko patches (cko3) from [http://kem.p.lodz.pl/~peter/cko/](http://kem.p.lodz.pl/~peter/cko/) 
I see that newest version is cko4 and I haven't tried it.

I've also succeeded with ubuntu source 2.6.11 with patch [ftp://ftp.namesys.com/pub/reiser4-for-2.6/2.6.11/reiser4-for-2.6.11-3.patch.gz](ftp://ftp.namesys.com/pub/reiser4-for-2.6/2.6.11/reiser4-for-2.6.11-3.patch.gz)
but I had to go back to original because there was some fs errors after about ten minutes of uptime that hang out the system (it didn't harm fs structure itself).
Maybe I should also use patch to upgrade from 2.6.11 to 2.6.11.3 ?

The only problem using original kernel is (as I've noticed) that it has problems unloading kernel modules at the boot time, but everything else works fine.

---

