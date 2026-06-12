---
title: "Removing Grub from a specific hard drive"
date: 2007-12-30
forum: General Help
---

### Post by m i k e on 2007-12-30
I did a dual boot of Ubuntu and Windows XP on the same SATA hard drive with partitions.  I installed Windows first and then Ubuntu.  Everything seemed to work just fine until I restarted and it booted directly into XP without showing me the Grub menu.  I tried manually installing Grub from the live CD.  This produced the Grub menu but gave me Error 22.  Then I thought what if I changed the bios so that it boots the other hard drive in the machine even though that one just had files on it.  Sure enough that was it.  Ubuntu had installed Grub there even though it wasn't the drive I was installing Ubuntu to.  So now the boot into Ubuntu works but my question is:

How can I remove Grub from the other hard drive so that it boots directly into Windows XP like it did before I tried to manually install Grub?  I believe it has to do with a booting the Windows CD and running fixmbr and/or fixboot but I don't know what the parameters should be for my specific setup and I don't want to just try it because I don't want to remove Grub from the wrong drive.  Please let me know what I would need to do.

If it would help to see a more specific description of my specific setup please refer to:  [http://ubuntuforums.org/showthread.php?t=653739](http://ubuntuforums.org/showthread.php?t=653739)

Thanks very much for any help.

---

### Post by Herman on 2007-12-30
Unless I'm mistaken, you installed Ubuntu in what you think is your first hard drive, (SATA), and GRUB didn't install there at all, because you were still booting into Windows.
Grub is in the IDE hard disk's MBR, is that right? Grub thiks that;s the first hard drive.  It's a data drive, and you switched the hard disk boot priority around in your BIOS, and now you are getting GRUB, and Ubuntu boots okay but not Windows. 
Is that right so far? :)

So Windows should still be in the MBR in your SATA hard drive. 

One way you could boot would be to try using your F8 key or your F12 key during boot-up, (whichever it is for your computer), and if your BIOS has the boot menu feature and it's enabled, you'll get a menu that allows you to select which device to boot and then which hard disk to boot.
In the long run you will probably find it a little slow and inconvenient to have to boot that way all the time though.

The other thing would be to install GRUB to the other hard disk's MBR as well, and switch your BIOS back the way it was before, then configure GRUB by editing your /boot/grub/menu.lst file.
Windows doesn't need the MBR to boot at all, GRUB will boot it by the boot sector. The MBR is not part of Windows, it's not even in the Windows partition, but comes before it.

---

### Post by Herman on 2007-12-30
Oh, okay, sorry, I just re-read your other thread again.
You do have GRUB on both hard drives.

Try this,
```
title        Ubuntu 7.10, kernel 2.6.22-14-generic
root        (hd[COLOR=Sienna]**0**[/COLOR],2)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=76b4e890-3302-47f7-bbfc-92659bbe551d ro quiet splash
initrd        /boot/initrd.img-2.6.22-14-generic
quiet

title        Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root        (hd[COLOR=Sienna]**0**[/COLOR],2)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=76b4e890-3302-47f7-bbfc-92659bbe551d ro single
initrd        /boot/initrd.img-2.6.22-14-generic

title        Ubuntu 7.10, memtest86+
root        (hd[COLOR=Sienna]**0**[/COLOR],2)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Microsoft Windows XP Professional
root[COLOR=Sienna]**noverify**[/COLOR]        (hd[COLOR=Sienna]**0**[/COLOR],0)
[COLOR=Sienna]** makeactive**[/COLOR]
savedefault
chainloader    +1
```
Switch your hard drives back to the way they used to be originally in your BIOS's hard disk boot priority so the SATA drive's MBR will be the one you'll be booting with.
Try that and tell me what happens. :)

---

### Post by Herman on 2007-12-30
....OR, to answer your question exactly, here's the best link I have found about how to use [Windows XP 'Recovery Console'.]("http://www.users.bigpond.net.au/hermanzone/p18.htm#Windows_XP_Recovery_Console")

But I think you'll have to switch your drives around in your BIOS to do that and then switch them back again.

---

### Post by m i k e on 2007-12-31
Thanks a lot.  That worked.

I booted into the Windows XP Recovery Console
-Typed "map" to find the path of the device which turned out to be "\Device\HardDisk1"
-Then typed "fixmbr \Device\HardDisk1"
-Then exited with "exit"

Worked perfectly however, if anyone reads this for help in the future be sure to to use the map command to find which drive you want to load the Windows bootloader to.  Had I just typed "fixmbr" without any parameters it would have erased the Grub setup that I wanted on the other drive which was mapped as "\Device\HardDisk0" whereas I wanted to overwrite "\Device\HardDisk1".

Thanks again.

---

