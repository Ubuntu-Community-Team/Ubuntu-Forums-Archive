---
title: "Grub boken, need help fixing please"
date: 2013-08-02
forum: General Help
---

### Post by failmaster on 2013-08-02
Hello All,

I run a dual boot through grub, Win7 and Ubuntu 12.04.

Silly AMD program decided to install a bunch of update, and silly me told it to go ahead. In the update were a bunch of drivers and, while it was not stated whatsoever, Norton Internet Security as well (I know I know, teh horror). 

I am suspecting that Norton did some stupid stuff like it always does, and nuked grub somehow.

When I boot it goes into the grub recovery mode, stating that device XYZ was cannot be found (no such device). I fired up a live cd, tried looking up resolutions and got to a popular askubuntu thread, where they have you mount your linux partition, then run grub-install.

This is the thread I used:
[http://askubuntu.com/questions/143667/boot-error-no-such-device-grub-rescue](http://askubuntu.com/questions/143667/boot-error-no-such-device-grub-rescue)

This did not fix my issues unfortunately.

Here is the output for fdisk -l

```

sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa1031c54

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848  1953519615   976656384    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x651c7375

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   103049215    51523584    7  HPFS/NTFS/exFAT
/dev/sdb2       103051262   156301311    26625025    5  Extended
/dev/sdb5       103051264   140644351    18796544   83  Linux
/dev/sdb6       140646400   156301311     7827456   82  Linux swap / Solaris

Disk /dev/sdc: 2055 MB, 2055207936 bytes
33 heads, 63 sectors/track, 1930 cylinders, total 4014078 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          32     4014077     2007023    6  FAT16

```


From what I have been able to see was that sda1 is my 1tb drive I use for storage, and sdb is my windows / linux drive. sdb5 being the Ubuntu partition.

I tried to download grub customizer, but it does not help me much as there are a bunch of ! and - next to a few items, and I am not so sure what I need to change them to.

I tried the above thread method on sda1 and sdb5. Doing it on sdb5 did nothing, doing it on sda1 changed the grub boot, now when I reboot and start up "normally" (not live cd) I still get grub, but a different version.

When I boot in the Live CD I can see and access through /mount/partition UUID all 3 of the "data" partitions, that is, my 1Tb storage, the windows and the linux partitions.

Not sure where to go from here, please help :)

---

### Post by failmaster on 2013-08-02
I have had a huge breakthrough, yet the problem is not 100% fixed yet.

Using the help from: [http://askubuntu.com/questions/284898/insmod-error-in-grub-symbol-not-foundgrub-realidt](http://askubuntu.com/questions/284898/insmod-error-in-grub-symbol-not-foundgrub-realidt)

I was able to get grub to load a menu, and from that menu, to get into ubuntu, or windows if I wanted to.

The following worked for me:



[LIST]
[*]Do a
ls (hd0,msdos5)/ 
ls (hd0,msdos6)/
[*]If you see grub then do a set prefix="(hd0,msdos5)/grub" where 5 needs to be changed to correct number.
[*]If you see boot then do a
set prefix="(hd0,msdos5)/boot/grub"
set root="(hd0,msdos5)"
where 5 needs to be changed to correct number.
[*]After changing prefix you need to do a
insmod normal
normal
[/LIST]


The problem is that even after doing "sudo update-grub" they changes do not stick, and I am thrown back to the grub recovery command line every time I reboot or power down.

Now, how do I make the changes stick for good?

---

### Post by GwL3eNC on 2013-08-02
Hi,

you wrote drive xyz not found. stands xyz for a long string containing letters and numers?
The following i see if open grub-customizer and view the properties of my system entry 
It's calles Ubuntu with Linux....

recordfail
gfxmode $linux_gfx_mode
insmod gzio
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set=root 731537af-b00f-40b0-a6af-ad923de06fd6
linux    /boot/vmlinuz-3.5.0-37-generic root=UUID=731537af-b00f-40b0-a6af-ad923de06fd6 ro   
initrd    /boot/initrd.img-3.5.0-37-generic

You can see the --set=root 731537af-b00f-40b0-a6af-ad923de06fd6 anf the other one in root=

Make shure that this numer in your text matches your starting patition. Find out
the UUID with

sudo blkid

/dev/sda1: LABEL="System" UUID="3654E63F54E6018B" TYPE="ntfs" 
/dev/sda5: LABEL="Sicherundsspeicher" UUID="F4EC80ACEC806AA6" TYPE="ntfs" 
/dev/sda6: UUID="822945b9-bc28-481a-affc-1b6b23d74ed0" TYPE="swap" 
/dev/sda7: UUID="731537af-b00f-40b0-a6af-ad923de06fd6" TYPE="ext4" 

and choose the number for the ext4 partition. Save after your changes.
Which you luck!

---

### Post by failmaster on 2013-08-02
Yea that number is correct, I don't think that was ever an issue.

What I see now is that there is an issue with multiple versions of grub looking for stuff in different places. I ran bootinfoscript-061 and the first few lines showed that it looks for core.img in a place that it probably should not:

============================= Boot Info Summary: ===============================


 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos2)/boot/grub on this drive.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.

===========================================================================

The second entry is the correct one, since it's /dev/sdb5/ which is my linux partition.

The first one is on my 1Tb drive which has no OSes on and is only for storage.

I think I need to remove that first entry, but not sure how to proceed.

If you could shed some light on that it would be great.

---

### Post by grahammechanical on 2013-08-02
So, you now have the means of loading Ubuntu? After running

```
sudo update-grub
```

did you notice from the output if it detected Windows 7? Was you using Grub to boot into both Ubuntu and Windows?

You need to install grub into the MBR of the disk

```
sudo grub-install /dev/sdb
```

Regards.

---

### Post by failmaster on 2013-08-02
Yea I did update-grub and grub-install a bunch of times both on sda and sdb and neither worked. I ended up finding out about boot-repair ([https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)).

Ran this with defaults and it fixed by boot issue. I now have to change around the menu, as some items were added that I did not want, but that is easy with grub customer.

If only I had found this wonderful tool (that can be run from a live cd at that!) it would have saved me 2h+ of work.

Glad this is over though!

Edit: actually now Ubuntu will not shut down or reboot anymore, I need to power cycle. Other than that, it fixed the problem.

Edit2: it will shut down now after a few forced reboots, probably just the ghost in the machine getting pissed I managed to get it working again. :)

---

### Post by GwL3eNC on 2013-08-02
Hi,

like mentioned above 
sudo grub-install /dev/sdb

is importend.

I cant find a simple solution to deinstall that one on sda. Seems one
possebility is [http://www.sysint.no/products/Download/tabid/536/language/en-US/Default.aspx](http://www.sysint.no/products/Download/tabid/536/language/en-US/Default.aspx)
but its ugly. Cant find anything else. You should take your sdb out of your pc, so that  sda ist the only
hd. But i'm realy not shure that this solves your problem.

If you got a windows cd you can use this
[http://superuser.com/questions/289490/can-i-erase-a-grub-bootloader](http://superuser.com/questions/289490/can-i-erase-a-grub-bootloader)

---

