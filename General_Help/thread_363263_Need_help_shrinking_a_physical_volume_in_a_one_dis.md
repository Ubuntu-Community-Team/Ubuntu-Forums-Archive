---
title: "Need help shrinking a physical volume in a one disk lvm setup"
date: 2007-02-16
forum: General Help
---

### Post by hannanjf on 2007-02-16
Ok, so I'm trying to free up space at the end of my laptop's hard drive in order to install another operating system (xp).  I currently have only Ubuntu on my disk using LVM.  Here is some system info:

```

jacob@localhost:~$ df -h
Filesystem                          Size     Used    Avail   Use%  Mounted on
/dev/mapper/Ubuntu-root    6.0G    2.7G    3.0G    48%    /
varrun                               248M    100K   248M    1%     /var/run
varlock                              248M    0         248M    0%    /var/lock
procbususb                        10M      116K   9.9M     2%    /proc/bus/usb
udev                                 10M       116K  9.9M      2%   /dev
devshm                             248M     0        248M     0%   /dev/shm
lrm                                    248M    18M    231M      7%   /lib/modules/2.6.17-11-generic/volatile
/dev/sda1                          228M     22M   195M      11% /boot
/dev/mapper/Ubuntu-home  66G      5.3G  58G        9%  /home

```

And:

```

jacob@localhost:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          31      248976   83  Linux
/dev/sda2              32        9729    77899185    5  Extended
/dev/sda5              32         216     1485981   82  Linux swap / Solaris
/dev/sda6             217        9729    76413141   8e  Linux LVM

```

I want to reduce the size of the Ubuntu-home logical volume and then shrink the physical volume to free up enough room for a /dev/sda7.  As I can gather, these are the steps to be taken:

[LIST=1]
[*]Shrink filesystem on /dev/Ubuntu/home with resize2fs.
[*]Shrink logical volume /dev/Ubuntu/home with lvreduce or lvresize.
[*]Shrink physical volume /dev/sda6 with pvresize.
[*]Shrink partition /dev/sda6 with fdisk.
[*]Use gparted to create new ntfs partition.
[/LIST]

So far, I can't get past step one....  /home is always busy.  Am I on track here?  Should I just give up and reinstall (although avoiding this was part of the reason I tried to use lvm in the first place.)?

---

### Post by Jaiinus on 2007-02-16
Have you tried unmounting /home? LVM is used mostly to ADD space to a full drive rather than dynamically shrink it.

---

### Post by hannanjf on 2007-02-16
Yeah, I have.  I always get "umount: /home: device is busy".  If I go around this with the "lazy" option (-l), I then get a busy message when I try to use resize2fs.

Yeah, it's clear from the documentation that it handles adding space better; I had intended to have a GNU/Linux only computer, but I'm getting pulled back into a dual boot situation (damn those waste-of-time video games....).  :-/

---

### Post by jamesjrl on 2007-02-17
You can't umount until all programs stop using the partition

make sure any apps using temp files in home are closed, also make sure you have no shell's open and residing in that area.

i'm guessing you will have to drop back out of X because the desktop is kept in /home

i'm having a siilar problem resizing my root currently
i have read around a bit, and may be able to help.

if you have some available external storage, maybe a usb hard drive maybe you could add a smaller volume to your group, lvmove your ubuntu-home to this volume, remove your current volume, then delete is and create a smaller one, add this new volume to group, lvmove stuff back and remove the external volume from group.
i have not tried this method, but it seems like this should work

long process huh... i have considered doing this with my root but if anything goes wrong mid way, then i wont be able to boot back :-/
which is also stopping me from migrating to a new disk i have bought, moving my system is not the major concern, it is that making this bootable is not sure fire, and as far as i can tell you have to move the data, can't see any way to copy.

---

### Post by keithweddell on 2007-02-17
Try doing this from a livecd that supports LVM.  Like RIP Linux.  Then your hard-drive partitions won't be mounted so you can use the lvm tools to resize.

Keith

---

### Post by jamesjrl on 2007-02-18
this looks it should work to me, all goes well on another test drive i created.
can shrink and then clone and it boots fine

Remember people, never keep a cloned lvm volume, the uuid's are cloned and confuse the hell out of things (possibly the reason for my other problem)

shame my actual root drive has some problem with its lvm yet undetermined

thanks anyhow

---

