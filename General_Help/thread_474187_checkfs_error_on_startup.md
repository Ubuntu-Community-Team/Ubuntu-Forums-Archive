---
title: "checkfs error on startup"
date: 2007-06-14
forum: General Help
---

### Post by danielfisica on 2007-06-14
I've got the following error on kubuntu 7 startup (from checkfs log file)

```

Log of fsck -C -R -A -a
Thu Jun 14 21:45:00 2007

fsck 1.40-WIP (14-Nov-2006)
fsck.ext3: No such file or directory while trying to open /dev/.tmp-254-2
/dev/.tmp-254-2:
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

/dev/mapper/hdb1: clean, 69694/526944 files, 490377/1052722 blocks
fsck died with exit status 8

Thu Jun 14 21:45:00 2007
----------------

```

can anyone tell me what is wrong?

---

### Post by geoffkaniuk on 2007-06-20
Hello danielfisica,

I have recently started having exactly the same problem as you report,  but with Feisty - Gnome.

I wonder if you have managed to solve your problem yet.

If you search the forum for 'fsck size'  you will see a thread started by me with various similar problems and various suggestions for a fix.  None of these have worked for me but  they might for you.

Its an annoying problem, but at least so far it has always booted using CTRL+D

---

