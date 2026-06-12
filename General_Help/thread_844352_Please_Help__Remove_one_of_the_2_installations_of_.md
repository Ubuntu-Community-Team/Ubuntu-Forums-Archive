---
title: "Please Help : Remove one of the 2 installations of Ubuntu on pc??"
date: 2008-06-29
forum: General Help
---

### Post by the mage on 2008-06-29
Heya everyone...I have installed 2 versions of ubuntu on my laptop, the 32 and 64 bit ones of the hardy edition...
I decided to go with the 1st only, and remove the other, and add the partition which it is in back to the 32 bit ubuntu partition...
Any help would be appreciated much. 
Manos

---

### Post by LunatikOwl on 2008-06-29
If you have some experience with partitions all you need to do is download [gParted LiveCD]("http://gparted.sourceforge.net/livecd.php"), burn and delete the partition of the unwanted installation and expand the other partitions to the new unallocated space avaliable. Then after you reboot to the ubuntu version you do want, edit the /boot/grub/menu.lst to remove the unwanted entries in the boot menu. 

Just better backup your system before you start doing any changes...

---

### Post by Elfy on 2008-06-29
If you are unsure which is which, boot the one you want to keep. Open a terminal and run this

```
cat /boot/grub/menu.lst
```

The buntu you are booting will be at the top, the one you longer require will be at the bottom - I think it will say something similar to

"Ubuntu -version blah blah located on sda5" obvioulsy the number will be different, but that will be the onle you can delete.

If you are still not sure and it's better to be safe than sorry, post your menu.lst and the output of

```
sudo fdisk -l
```

---

### Post by adityam on 2008-07-01
Hi,

I am in a similar situation. I installed ubuntu 7.10 on one partition. While testing hardy, I installed it on another partition. After I was sure that I liked hardy, I updgraded from gusty to hardy on my first partition. 

The trouble that I have is that I get the boot menu from the second installation. It has the wrong kernel numbers for the old partition (basically the same kernel numbers that were present when I first installed hardy on the second partition). So, the menu.lst from the second partition is being used, rather than the menu.lst from the first partition. Will reformatting the second partition make my system unbootable?

I am currently booted into the partition that I want to keep.

Here is the output of fdisk -l

[HTML]
Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfdf8bf47

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         794     6372352   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2             795        1159     2925720   82  Linux swap / Solaris
Partition 2 does not end on cylinder boundary.
/dev/sda3            3590       12161    68848920    5  Extended
Partition 3 does not end on cylinder boundary.
/dev/sda4            1159        3590    19527480   83  Linux
Partition 4 does not end on cylinder boundary.
/dev/sda5            4866       12161    58597497   83  Linux
/dev/sda6   *        3590        4866    10251297   83  Linux
[/HTML]

I am also attaching the menu.lst file. Any suggestions?

---

### Post by Elfy on 2008-07-01
@adityam - I would use either the livecd and these insrtuctions to set grub up again or get supergrub, burn it an iso and boot with that.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Using](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Using) the Ubuntu Desktop/Live CD

Then you will have grub on the right disc and you can do as you will with the partition.

---

### Post by adityam on 2008-07-01
> **forestpixie said:**
> @adityam - I would use either the livecd and these insrtuctions to set grub up again or get supergrub, burn it an iso and boot with that.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Using](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Using) the Ubuntu Desktop/Live CD

Then you will have grub on the right disc and you can do as you will with the partition.

Thanks. These instructions worked perfectly. I now see the grub from sda3, so I can reformat sda5. :)

Aditya

---

