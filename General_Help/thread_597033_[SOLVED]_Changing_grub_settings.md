---
title: "[SOLVED] Changing grub settings"
date: 2007-10-30
forum: General Help
---

### Post by Occas on 2007-10-30
Hi guys,

I have 64 bit Ubuntu 7.10 installed and at first I was getting error 17s before it even got to the Grub OS selection screen. I am dual booting with Windows XP. They are on separate hard drives.

I used a Super Grub CD to reset my grub and now it boots to the OS selection screen.

If I select Windows it runs fine.

If I select the "normal" Ubuntu option I get error 17.

If I press (e?) to edit the "normal" Ubuntu option it tells me the boot is on (1,0) which is incorrect.

I can manually edit it to say (3,0) and then press b to boot the correct drive and off I go.

It hasn't appeared to save the change however, and I have to re-edit it each time I boot in.

I have looked at quite a few posts on editing settings, but as I am new to Ubuntu (5 days!) I am now starting to get confused as to which entry I should be editing.

If I type either "/boot/grub/stage2" or "/boot/grub/stage1" I get results of (3,0) but that is now that I have booted in manually by doing what I have detailed above, so I'm not sure if that is reflecting what the Grub settings truly are, or what the system is seeing as I have (seemingly) only temporarily edited them.

This is what I get when I type "cat /boot/grub/menu.lst"

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=47ac646b-1fa3-4006-9ac7-dd1ea35a881c ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=47ac646b-1fa3-4006-9ac7-dd1ea35a881c ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd1,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

Here is my "sudo fdisk -l"

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xaab12ed5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       24321   195358401    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ffc810

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xaa471f8f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       38161   306528201   83  Linux
/dev/sdc2           38162       38913     6040440    5  Extended
/dev/sdc5           38162       38913     6040408+  82  Linux swap / Solaris

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7c404f9f

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/hda2            2551        9728    57657285    f  W95 Ext'd (LBA)
/dev/hda5            2551        9728    57657253+   7  HPFS/NTFS



So should I be editing all the menu.lst entries from (1,0) to (3,0)?

Cheers!

Shaun

*UPDATE*

I went ahead and edited the menu.lst entries, saved and restarted.

Now it has (3,0) correct if I view the root entry.

However, It gets part way to loading and crashes:

"PCI: Canot allocate resource region 0 of 0000:00:040
Ramdisk: ran out of compressed data
invalid compression format (err=1)
Kernal panic-not synching: VFS: Unable to mount root fs on unknown - block (0,0)

If I run it using the 2nd "recovery" option I also get:
"Please append a correct "root=" boot option"
in between the "Invalid" and "Kernal" lines above.

---

### Post by Occas on 2007-10-31
24(ish) hour bump

Thanks guys...

---

### Post by meierfra on 2007-10-31
It looks like your "UUID"'s  in menu.lst are wrong.


Use 

"sudo blkid" to find the correct UUID.

You might also try to replace

root=UUID=47ac646b-1fa3-4006-9ac7-dd1ea35a881c

by 

root=/dev/sdc1

---

### Post by Occas on 2007-10-31
Thanks a lot for your reply.

I'll give it a shot now and let you know how I go!

Shaun

---

### Post by louieb on 2007-10-31
If you can edit the grub boot prompt and it works then make the same change to /boot/grub/menu.lst. Heres how to open the file for editing. [Nuts Ubuntu FAQ]("http://louboldt.com/ilinuxmisc.htm")

---

### Post by Occas on 2007-10-31
Thanks for your help guys! :)

I checked the correct UUID settings and they were correct. I also attempted the change to "root=/dev/sdc1".

Unfortunately neither worked, however since it was a new install I decided to cut my losses and try a re-install, which has worked flawlessly.

Now to search the forums to get my boot and shutdown screens working. It's not my screen resolution setting as that is within my monitors capabilities.

Onward!!! :)

Shaun

---

