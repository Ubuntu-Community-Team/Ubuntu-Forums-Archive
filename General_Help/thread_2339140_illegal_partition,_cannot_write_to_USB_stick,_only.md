---
title: "illegal partition, cannot write to USB stick, only Read Only mounting."
date: 2016-10-05
forum: General Help
---

### Post by Dlanor_S. on 2016-10-05
Dear people,

I've been searching high and low for a solution just to delete / format and create a new partition table to a USB stick, but to no avail.
It just won't accept writing to it.
I hope there are some possible solutions to this issue, but let me write down what I tried so far.

Gparted (trying to delete / format) = application hangs.
DCFLDD (trying to write zeros) = 'Terminal' hangs.
Parted Magic Live CD (Format Disk options) = all fail and hang.
Spinrite (won't even boot to read out and try to fix it)
DBan Nuke = crashes when wanting to write zeros.
CAT (writing zeros) = 'Terminal' hangs.

Now what I managed to accomplish is to mount the USB stick in Read Only mode.
I could see all my files so I recovered them all.

I merely want to blank it, but it doesn't allow me on any OS I have tried so far (OS X, Windows, Linux)

Any suggestions?

Regards,
Dlanor

---

### Post by TheFu on 2016-10-05
Sometimes flash drives wear out. If it is over a year old, that would be my guess.  [https://superuser.com/questions/175524/what-actually-happens-with-an-usb-flash-drive-when-it-dies](https://superuser.com/questions/175524/what-actually-happens-with-an-usb-flash-drive-when-it-dies) The cheaper the flash, the shorter the lifespan because the vendor didn't add the extra HW to attempt load leveling of the used flash memory.

If you've never used the flash drive in this computer, with this port, it could be a simple USB chip/flash drive chip incompatibility. That does happen. I haven't found a way to determine which flash devices will work with which USB ports/chips. Price is NOT a good indicator from my experience.

Or it could be something else, but that's all I got.

If I just want to be certain it is destroyed - a drill works. ;)

---

### Post by Dlanor_S. on 2016-10-06
Thank you for your reply.
It is somewhat an old thing, though hardly used and I think it got corrupted when a Windows Machine got "borked" while the stick was still mounted.

I do managed to get fdisk to delete and write a new MBR, so writing a piece of the flash worked again.
Now with dcfldd it only does a part of the drive and stops, which was more than before.

Anybody else got any ideas?

Cheers.

---

### Post by colmax on 2016-10-06
Some firmware will only recognise up to 32GB
If the usb drive is larger it will only go to it's limit and leave the rest unused
maybe just delete data instead of format
Cheers

---

### Post by sudodus on 2016-10-06
Welcome to the Ubuntu Forums :-)

You could try yet another tool, which can repair the pendrive, if it is a corrupted partition table or file system. ***mkusb*** wipes the first megabyte, and after that creates a new partition table and file system. Select the 'standard', if you want to use the drive as a standard storage drive. See the following links,

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
[mkusb/wipe](https://help.ubuntu.com/community/mkusb/wipe)

Before discarding the pendrive, please test it in some other computer(s); it might work with other hardware and/or other software.

If still no luck, I'm afraid there is no tool for normal users, that can save your drive. See this [link about pendrive lifetime](http://ubuntuforums.org/showthread.php?t=2196858&p=13199297#post13199297).

---

