---
title: "Fdisk System"
date: 2007-06-20
forum: General Help
---

### Post by SteveF on 2007-06-20
I never paid attention to this before, but I ran sudo fdisk -l recently to work on another problem.  The output surprised me and I was wondering if someone knew anything about this.  Here is the output:

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4865    39078081    7  HPFS/NTFS

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1216     9767488+   c  W95 FAT32 (LBA)
/dev/sdb2            1217       30515   235344217+   f  W95 Ext'd (LBA)
/dev/sdb5            1217       17020   126945598+   7  HPFS/NTFS
/dev/sdb6   *       17021       18236     9767488+  83  Linux
/dev/sdb7           18237       19452     9767488+  83  Linux
/dev/sdb8           30334       30515     1461883+  82  Linux swap / Solaris
[COLOR="Blue"]/dev/sdb9           19453       30333    87401601   82  Linux swap / Solaris[/COLOR]

I highlighted the last one, because that is the one confusing me.  This drive was formatted using ext3.  So I'm confused as to why it shows up as Linux Swap.

Any thoughts and is this a problem that needs to be fixed?

Thanks,

Steve

---

### Post by mopey on 2007-06-20
That's not a problem.  That partition actually isn't formatted as ext3, it's your swap partition.

[http://en.wikipedia.org/wiki/Virtual_memory](http://en.wikipedia.org/wiki/Virtual_memory)

---

### Post by mopey on 2007-06-20
Ooops sorry, misunderstood.

Let me look at it some more.

---

### Post by mopey on 2007-06-20
So, uh.

/dev/sdb6 * 17021 18236 9767488+ 83 Linux
That's your /boot I'm guessing

/dev/sdb7 18237 19452 9767488+ 83 Linux
This is your /?

/dev/sdb8 30334 30515 1461883+ 82 Linux swap / Solaris
This is your swap?

/dev/sdb9 19453 30333 87401601 82 Linux swap / Solaris
So, why 2 swaps?  This obviously isn't ext3, right?  But it will still boot and work without it, it will just be mounted on sdb7.

What is the output of df?

---

### Post by SteveF on 2007-06-20
sdb6 is a Kubuntu install (Edgy) and is where grub looks for the menu.  I have to switch grub to sbd7 at some point.
sdb7 is my Ubuntu install (Feisty) and is where I'm running the commands
sdb8 is my swap
sdb9 has data on it and was formatted as ext3 (is there any way to verify this?)

output from df
[FONT="Courier New"]Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdb7              9614116   5909824   3215920  65% /
varrun                  257780       128    257652   1% /var/run
varlock                 257780         0    257780   0% /var/lock
procbususb              257780       152    257628   1% /proc/bus/usb
udev                    257780       152    257628   1% /dev
devshm                  257780         0    257780   0% /dev/shm
lrm                     257780     33788    223992  14% /lib/modules/2.6.20-16-generic/volatile
/dev/sdb1              9757936   6732216   3025720  69% /staging
/dev/sdb9             86029856  74649056   7010720  92% /data
[/FONT]

---

