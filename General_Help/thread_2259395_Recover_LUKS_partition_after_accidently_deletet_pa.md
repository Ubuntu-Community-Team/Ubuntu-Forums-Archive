---
title: "Recover LUKS partition after accidently deletet partition table with gparted"
date: 2015-01-04
forum: General Help
---

### Post by s-bamberger on 2015-01-04
Hi guys,

I deleted my partition table with gparted when I was distracted while I thought I work on my raspberry pi so shame on me. I know that this was posted at least once before here 

[http://ubuntuforums.org/showthread.php?t=1643334](http://ubuntuforums.org/showthread.php?t=1643334)

So I did this:

```
mint@mint /mnt $ sudo losetup -o 0xf500000 -r -f /dev/sda
mint@mint /mnt $ sudo losetup -a
/dev/loop1: [0005]:7471 (/dev/sda), offset 256901120
mint@mint /mnt $ sudo cryptsetup luksOpen /dev/loop0 luksrecover
Enter passphrase for /dev/sda: (input was correct YEAH)
mint@mint /mnt $ sudo mount -o ro /dev/mapper/luksrecover /mnt/recover
mount: unknown filesystem type 'LVM2_member'
```

so what is wrong?

Additional information can be found here 

[http://unix.stackexchange.com/questions/177070/lvm-encrypted-partition-without-partition-table](http://unix.stackexchange.com/questions/177070/lvm-encrypted-partition-without-partition-table)

---

### Post by LostFarmer on 2015-01-04
First let me say, have no knlowlege on what you need to do, but looking at losetup commands your problem might be:
losetup -a    --Show the status of all loop devices,  In your case it would seem /dev/sda offset 0xf500000 is at /dev/loop1 but your next command you use /dev/loop0.  Try  ```
sudo cryptsetup luksOpen /dev/loop[COLOR=#ff0000]1[/COLOR] luksrecover
```

---

### Post by s-bamberger on 2015-01-04
```
mount -o ro,noload /dev/mapper/mint--vg-root /media/whatever 
```

helped, now I can backup my data. 

But i don't know how to make a new partition table, so it will work again like in the past. 

thanks

---

### Post by gedakc on 2015-01-06
You might try [Testdisk]("http://www.cgsecurity.org/wiki/TestDisk") to scan the surface of the disk in an attempt to rebuild the partition table.

Prior to doing that I highly recommend backing up as much of your data as possible.

---

### Post by andrea48 on 2015-01-06
> **s-bamberger said:**
> ```
mount -o ro,noload /dev/mapper/mint--vg-root /media/whatever 
```

helped, now I can backup my data. 

But i don't know how to make a new partition table, so it will work again like in the past. 

thanks

how that help? I am having [same issue here]("http://ubuntuforums.org/showthread.php?t=2259718"), trying to recover a luks volume and getting the 
```
 unknown filesystem type 'LVM2_member'
```

How did u do?

---

