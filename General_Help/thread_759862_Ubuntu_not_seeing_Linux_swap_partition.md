---
title: "Ubuntu not seeing Linux swap partition"
date: 2008-04-19
forum: General Help
---

### Post by thecoolcat on 2008-04-19
Hello,

I upgraded my harddisk from 40GB to 400GB on my desptop with XP and Gutsy dual boot. Now that I got plenty of space I decided to organize things better. In my original config, I had 4 primary partitions in the following order:
FAT32 (small, I think for DOS?)
NTFS (for XP)
linux swap
ext3 (for Ubuntu).

Using sys rescue cd and gpartedI I deleted linux swap and moved ext3 as my 3rd primary partition and changed my 4th to be extended. Here's how my new partitions look:

FAT32 (unaltered)
NTFS (XP boot, Now larger)
ext3 (Ubuntu, Moved and larger)
Extended:
   Linux swap
   NTFS (for data)
   ext3 (for data)

After this change, both windows and linux boot fine, but in Ubuntu, I don't see linux swap space. When I hit top, this is what I see:
> 
Mem:   1295160k total,   971712k used,   323448k free,   220024k buffers
Swap:        0k total,        0k used,        0k free,   258964k cached


This is what my /etc/fstab contains:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=12488622-45af-48b9-b289-dcfcef975bd5 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=07D3-0A0D  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=AC60D2FB60D2CAEA /media/sda2     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda3
UUID=67dc7470-24b4-4359-929c-ed80cfa352f6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/

Can someone help me with restoring linux swap?
Thanks.

---

### Post by Diabolis on 2008-04-19
Have you checked if the uuid numbers are correct?

```
blkid
```

or

```
ls -l /dev/disk/by-uuid/
```

---

### Post by thecoolcat on 2008-04-19
Hah:
Seems like they don't match. In /etc/fstab, UUID for swap space points to (I think)
> # /dev/sda3
UUID=67dc7470-24b4-4359-929c-ed80cfa352f6 none            swap    sw              0       0

blkid shows this:
> $ blkid
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D3-0A0D" TYPE="vfat" 
/dev/sda2: UUID="AC60D2FB60D2CAEA" TYPE="ntfs" 
/dev/sda4: UUID="12488622-45af-48b9-b289-dcfcef975bd5" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="57580daa-5e2f-4fd1-ab90-87e41bfe1c8c" 
/dev/sda6: UUID="77471984776FFE73" TYPE="ntfs" 
/dev/sda7: UUID="68e83aef-729f-42aa-b5ad-a87e6be2b30f" TYPE="ext2" 
$ ls -l /dev/disk/by-uuid/
total 0
lrwxrwxrwx 1 root root 10 2008-04-19 01:53 07D3-0A0D -> ../../sda1
lrwxrwxrwx 1 root root 10 2008-04-19 01:53 12488622-45af-48b9-b289-dcfcef975bd5 -> ../../sda4
lrwxrwxrwx 1 root root 10 2008-04-19 01:53 57580daa-5e2f-4fd1-ab90-87e41bfe1c8c -> ../../sda5
lrwxrwxrwx 1 root root 10 2008-04-19 01:53 68e83aef-729f-42aa-b5ad-a87e6be2b30f -> ../../sda7
lrwxrwxrwx 1 root root 10 2008-04-19 01:53 77471984776FFE73 -> ../../sda6
lrwxrwxrwx 1 root root 10 2008-04-19 01:53 AC60D2FB60D2CAEA -> ../../sda2


How do I fix this? Can I edit fstab manually or is there an automated way to fix this?
Thanks!

---

### Post by bodhi.zazen on 2008-04-19
I do not see sda3 ???

At any rate, no you have to edit fstab manually. You may convert from UUID=xxx-yyy-zzz to /dev/sda3

---

### Post by thecoolcat on 2008-04-19
I don't know why /dev/sda3 is missing. In fact, I don't see sda6, sda7 where I got NTFS data and ext3 data.
For now, I just edited fstab to contain the correct UID of swap space. Let me reboot and see,

---

### Post by thecoolcat on 2008-04-19
After rebooting, I do see swap space (after I edited fstab). Now I'm not sure if this swap will be used. "top says 0 used. May be I should try some memory intensive applications.

Now should I edit fstab to contain other entries as well?

---

### Post by Diabolis on 2008-04-19
Yes you can edit fstab as you please.

In my opinion uuid numbers are better over routes like /dev/sdax. Because uuid never change and routes change depending on the order in which you plug in devices.

Swap won't be used until you have opened and closed lots of files. This will take longer if you have a big RAM.

---

### Post by bodhi.zazen on 2008-04-19
> **thecoolcat said:**
> I don't know why /dev/sda3 is missing. In fact, I don't see sda6, sda7 where I got NTFS data and ext3 data.
For now, I just edited fstab to contain the correct UID of swap space. Let me reboot and see,

LOL Rebooting is soooo Mindows :lolflag:

```
sudo mount -a
```

> **thecoolcat said:**
> After rebooting, I do see swap space (after I edited fstab). Now I'm not sure if this swap will be used. "top says 0 used. May be I should try some memory intensive applications.

Now should I edit fstab to contain other entries as well?

Open a terminal and type :

```
free
```

If you swap is listed it is available but unused (not needed at this time) and you are done.

UUID will change when the partition is formatted as often happens when you install a new distro (it recognizes and re-formats swap). You hard drives should not change device names all that often, although removable devices will.

---

### Post by thecoolcat on 2008-04-19
Alright. I guess I'll edit fstap to include other entries as well (sda6 and sda7). Thanks all for your help.

---

