---
title: "Swap question"
date: 2007-01-18
forum: General Help
---

### Post by canadianwriterman on 2007-01-18
I'd like a better understanding of the Linux swap partition. If I have two distros on my HD, do they share the same swap partition or do I have to have two separate swap partitions? Probably a dumb question.

---

### Post by rocknrolf77 on 2007-01-18
You can use one swap for several distros. Just remember that the hibernation writes to swap.

---

### Post by canadianwriterman on 2007-01-18
Thanks rocknrolf77. One further question: when I install another distro, do I have to do anything to make both distros recognize and use the common swap partition, or is automatic? Thanks.

---

### Post by taurus on 2007-01-18
That distro should pick up your swap partition (82) automatically.  If not, you can either tell it then or add an entry in /etc/fstab later.

---

### Post by canadianwriterman on 2007-01-18
Many thanks. I have XP, Ubuntu and Kubuntu on my HD now. In fstab the swap does not appear as "82" unless I'm reading it wrong:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=91e7eb0e-78ba-4c00-9879-2853bc786ffc /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=fa420bda-8978-47af-824c-8632648579a0 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/sda2  /media/windows_ntfs  ntfs  nls=utf8,umask=0222  0  0

---

### Post by taurus on 2007-01-18
When I said 82, I meant the partition ID.  Linux partition has an ID of 83 while swap as an ID of 82.  Your swap is working fine now.

```

UUID=fa420bda-8978-47af-824c-8632648579a0 none swap sw 0 0

```
To check it, look at the output of this command.

```
free
```

---

### Post by canadianwriterman on 2007-01-18
Thanks for the clarification. I used the command "free" and the result was:

             total       used       free     shared    buffers     cached
Mem:       1035500     531040     504460          0      24752     279004
-/+ buffers/cache:     227284     808216
Swap:            0          0          0

I hope that doesn't mean there is zero swap memory.

---

### Post by taurus on 2007-01-18
Open a terminal and edit your /etc/fstab.

```
gksudo gedit /etc/fstab
```
Replace this line 

```
UUID=fa420bda-8978-47af-824c-8632648579a0 none swap sw 0 0
```
with this line.

```
/dev/sda5   none   swap   sw   0   0
```
Save it and reboot.  Now, what does this command look like?

```
free
```

---

### Post by canadianwriterman on 2007-01-18
Mmmm. Much the same:

Mem:       1035500     422560     612940          0      11220     241468
-/+ buffers/cache:     169872     865628
Swap:            0          0          0

I also just booted into my Kubuntu install and saw memory numbers in the "swap" line of the output. I guess that would explain why I have some freezing problems and over-usage of memory in Ubuntu. It appears there is no swap memory.

---

### Post by taurus on 2007-01-18
What's the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by canadianwriterman on 2007-01-18
It get:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1111     8924076    c  W95 FAT32 (LBA)
/dev/sda2            1112        7190    48829567+   7  HPFS/NTFS
/dev/sda3            7191       19956   102542895   83  Linux
/dev/sda4           19957       30401    83899462+   5  Extended
/dev/sda5   *       19957       30023    80863146   83  Linux
/dev/sda6           30024       30401     3036253+  82  Linux swap / Solaris

---

### Post by taurus on 2007-01-18
D'OH!

Your swap partition is /dev/sda6, not /dev/sda5...  /dev/sda5 is another Linux partition.

```
/dev/sda6   none   swap   sw   0   0
```

---

### Post by canadianwriterman on 2007-01-18
Yes, you're right. I should have caught that. "free" now shows:

             total       used       free     shared    buffers     cached
Mem:       1035500     371784     663716          0      10252     213332
-/+ buffers/cache:     148200     887300
Swap:      3036244          0    3036244

Thanks for walking me through that taurus!

---

### Post by taurus on 2007-01-18
So, looks like you have 1GB of RAM and about 3GB of swap!  ;) 

Don't forget to change that in Kubuntu, too.

---

### Post by canadianwriterman on 2007-01-18
Much appreciated. I fly again!

---

