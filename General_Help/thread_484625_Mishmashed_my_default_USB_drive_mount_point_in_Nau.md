---
title: "Mishmashed my default USB drive mount point in Nautilus"
date: 2007-06-26
forum: General Help
---

### Post by Nem Chua on 2007-06-26
Hello all,

I have made a blunder and wish for help. :(

On the desktop (Gnome/Nautilus), I right-clicked an USB partition and edited the drive (not partition) default mount point like this:
[IMG]http://www.transmekong.com/xresources/Screenshot.png[/IMG]

But I wrote something like "/media/external" as it is an external disk, which I am being told is wrong (should not have any slashes), so the USB drive cannot mount anymore. Of course, as they don't mount, I can't right-click and open the properties anymore. :-k

Help me! How can I correct this usb drive default mount point? Is there a config file somewhere? Is it likely that reinstalling while keeping my /home partition would save the day?

---

### Post by Nem Chua on 2007-06-26
So I reinstalled and found no change. the default mount point for an USB drive is most probably stored in a .something file on my home folder.

But where? :-k

Anyone got an idea?

---

### Post by merlinus on 2007-06-26
Have you looked for something in /etc/fstab?

-merlin

---

### Post by Nem Chua on 2007-06-26
Yes, fstab only lists the partitions I have by default on the machine, so only a sata/scsi drive and one line (why oh why?) about scd0, the CD ROM drive (and I am not going to tweak that one, last time was a hard time).

Here is, for the sake of being thorough:
```
cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=7fb976c7-e936-4f11-8e24-5d07f973afda /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda6
UUID=0d182701-69a2-47ef-a327-f9786d2006bb /home           ext3    defaults        0       2
# /dev/sda1
UUID=2FC7-FE65  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=A0E2-3DAA  /media/sda2     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=435d6b30-bd7f-4ae0-b0ac-9e7560d5b393 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
```

I suppose that should be taken care of by udev, so I am scanning the files in /etc/udev but so far nothing.

Would you have any other ideas?

(and, thanks merlinus for replying: it's heartening)

---

### Post by Nem Chua on 2007-06-26
Well, no luck with /etc/udev.

As we mentioned, it must be stored somewhere in my home directory, as it survived reinstalling.

:-k

in which dot file or folder should such info be stored?

---

### Post by Nem Chua on 2007-06-26
Digging ever deeper, I find:

[LIST]
[*]~/.gconfd/saved_state holds coded information including a line starting: ADD 3741319222 "def" "/apps/gnome-settings/nautilus" "IOR:0100000017000....." etc. and a lot of other lines starting by: ADD 1711276063 "def" "/desktop/gnome" "IOR:..." and the like, which might be relevant
[*]~/.nautilus holds many saved-session-ABCDEF files and a folder "metafailes" where I find url-encoded reference to some files including file:///media/usbdisk-2 which I used to have access to.
[*]~/.gnome2 holds a number of files and folders but nothing in there. Does anyone know what the eog-5FSR2K-style files are for? I had a pang when I found ~/.gnome2/hal-device-manager (looks so what I looked for ](*,) ) but nothing there either.
[/LIST]

I feel I am quickly reaching my limits here. Does anyone have another idea?

---

### Post by merlinus on 2007-06-26
A few more ideas:

If you plug in the external drive, are there any entries in /media besides your sda# partitions?

Have you checked System/Preferences/Removable Drives and Media, in terms of which boxes are ticked?

-merlin

---

### Post by Nem Chua on 2007-06-26
OK, I found a way. Stupid me, I should have tried this first. ](*,)

I just mounted the same usb drive using root and it did appear on the desktop, so I could right-click and correct the shot.

So simple I had to reinstall (not over yet) to come to this simple end.#-o

---

### Post by Nem Chua on 2007-06-26
Merlinus, I just see your post and OK, there are tools there I did not look at, yet I did not see the default mount point in there. I'll give it a more thoroug look now.

For the sake of completion, no, there was nothing new in /media when I plugged it on.

Thanks anyway: it's always easier when discussing with someone open-minded,
and hey! We did great in the end. :popcorn:

How do I add "solved" in the title?

---

