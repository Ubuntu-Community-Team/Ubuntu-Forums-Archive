---
title: "Resize Luks Volume inside Extended Partition"
date: 2014-11-22
forum: General Help
---

### Post by Elliot_Berg on 2014-11-22
Hi,

So the long and the short of it is that after removing an old Windows install etc I've been left with some free space on my disk which I'd really like to add to my / partition - the issue is I can't work out how to resize & move the partition to make use of it. I know Gparted doesn't work with Luks volumes, but for the sake of visualisation this is what it shows;

[IMG]http://blog.elliotberg.co.uk/disk.png[/IMG]

sda5 is /boot, sda6 is /, and sda7 is swap. I want to grow sda6 to make use of that extra free space before it. If I can grow and move the partition then I know I'll need to resize the filesystem after the event, but I'll cross that bridge when I come to it!

If it's useful to anyone, this is the output of fdisk;

Disk /dev/sda: 256.1 GB, 256060514304 bytes
255 heads, 63 sectors/track, 31130 cylinders, total 500118192 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3c2311d4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda3            2048   500117503   250057728    5  Extended
/dev/sda5            4096      587775      291840   83  Linux
/dev/sda6       168359936   480858111   156249088   83  Linux
/dev/sda7       480860160   500117503     9628672   83  Linux

and this is the output of sfdisk -d;

Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=        0, size=        0, Id= 0
/dev/sda2 : start=        0, size=        0, Id= 0
/dev/sda3 : start=     2048, size=500115456, Id= 5
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start=     4096, size=   583680, Id=83
/dev/sda6 : start=168359936, size=312498176, Id=83
/dev/sda7 : start=480860160, size= 19257344, Id=83

Thanks in advance for any help you're able to offer!

Elliot

---

### Post by Elliot_Berg on 2014-11-26
Hi,

So I decided to go ahead and give it a go, knowing I had pretty extensive backups if things went really wrong. Turns out that if you vaguely know what you're doing and are prepared to spend a bit of time on it, then this was really very do-able - if anyone knows how I could have done it slightly better then I'd still be interested to hear it, but I've achieved what I needed to now. If you're interested, I've documented it here; [https://blog.elliotberg.co.uk/blog/resizing-a-luks-partition-from-inside-an-extended-partition](https://blog.elliotberg.co.uk/blog/resizing-a-luks-partition-from-inside-an-extended-partition). I'd copy it into this post, but there's really quite a lot of text there!

Thanks anyway,

Elliot

---

