---
title: "Adding freespace to a partition"
date: 2007-07-21
forum: General Help
---

### Post by King_Critter on 2007-07-21
Ok, a while ago I split my main Ubuntu partition into 2 -- I was going to install Windows on the new one, but that never worked out. So I booted into the Feisty live CD and started up gparted... only to discover that it wouldn't let me delete the new partition. The exact error was "Please unmount any logical partitions having a number higher than 5." So I need help with that, too. But anyways, I did resize that partition, down to as low as it would go (around 700 MB). Now how do I add all the unallocated space back to my main partition?

---

### Post by kirios on 2007-07-21
[COLOR="Sienna"]Can you post the contents of your /etc/fstab?[/COLOR]

---

### Post by King_Critter on 2007-07-21
> unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda6 swap swap defaults 0 0

That's from my Live CD, at any rate -- would it be diferent if I booted into my install?

---

### Post by King_Critter on 2007-07-21
Ah yes, it is: 

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=daa4f29f-ab68-4749-b5a9-75e57d9868c0 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=954cbb1c-d47b-4606-988e-12fc3027414c none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by King_Critter on 2007-07-21
Erm... can anyone help me here?

---

### Post by meierfra on 2007-07-21
post the output of 

```
sudo  fdisk -l 
```

(l is a lower case L)

---

### Post by meierfra on 2007-07-21
I recommend using the Gparted live cd  to do the partitioning ( rather than  the gparted on the ubuntu live cd). It is more powerful, and avoids the problem of having mounted partitions). You can get the Gparted  iso at:


[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828&release_id=519163]("http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828&release_id=519163")

---

### Post by King_Critter on 2007-07-22
> Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4864    39070048+  83  Linux
/dev/sda2            4865        9729    39078112+   5  Extended
/dev/sda5            4865        4959      763056   83  Linux
/dev/sda6            9328        9729     3229033+  82  Linux swap / Solaris

I'll try the Gparted CD -- thanks for the link.

---

### Post by bodhi.zazen on 2007-07-22
It looks like the problem is with your swap partition (you can not resize or delete a mounted partition and swap is being mounted via the feisty CD)

So you can either boot the gparted live cd, or , if you want to use the feisty (cd or hard drive) unmount you swap with :

```
sudo swapoff -a
```

You should the be able to move/resize

Update fstab with the new swap partition (don't forget this step) and then :

```
sudo swapon -a
```

---

### Post by kirios on 2007-07-22
[B][COLOR="Sienna"]Sorry, I was working today and didn't have time to log on again. 
Bodhi, how do you update /etc/fstab with this UUID system? It used to be more intuitive with the older fstab layout.[/COLOR][/B]

---

### Post by bodhi.zazen on 2007-07-22
> **kirios said:**
> [B][COLOR="Sienna"]Sorry, I was working today and didn't have time to log on again. 
Bodhi, how do you update /etc/fstab with this UUID system? It used to be more intuitive with the older fstab layout.[/COLOR][/B]

Yea, but UUID has some advantages once you convert your mindset ...

you can either change format to (make sure the partition name has not changed) :

/dev/hdxy swap                    swap    defaults        0 0

where hdxy is the swap partition, 

Or list your partitions with : ```
blkid
``` and update your UUID.

---

### Post by kirios on 2007-07-22
[COLOR="Sienna"]Thanks! Have been wondering about that for a while but never got around to asking before. :-)[/COLOR]

---

