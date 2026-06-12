---
title: "GRUBless"
date: 2006-09-15
forum: General Help
---

### Post by sprinkles on 2006-09-15
Hello.
Way back, I had Windows 2000 running on it's own. I then installed Ubuntu on a different partition. The Windows 2000 installation became corrupted, so I installed XP, which wiped the MBR and i lost GRUB.
For a while I ha a lost Ubuntu partition, but I used "Super GRUB disk" to recover GRUB. It didn't thoug, it just wiped the WIndows bootloader, and now the system just shows a white flashing line after it looks for bootable disks. I can get into Windows and Ubuntu from the disk, but how do I instal GRUB?

---

### Post by Johan! on 2006-09-15
sudo grub-install /dev/hda

You can do this from the live cd.
Change /dev/hda if you have an other configuration.
Try sudo fdisk -lu to see a list of your disks/partitions.

---

### Post by wieman01 on 2006-09-15
Have you got a Ubuntu LiveCD? Then try this:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

If not you can also try a Windows 98 CD, boot, and format your MBR to get your Windows partition back:
> fdisk /mbr

---

### Post by sprinkles on 2006-09-15
> **Johan! said:**
> sudo grub-install /dev/hda

You can do this from the live cd.
Change /dev/hda if you have an other configuration.
Try sudo fdisk -lu to see a list of your disks/partitions.

I have sort of progress with this.

I now get a GRUB menu on boot, but the "Other operating system" is Windows 2000 Professional :( 

I chose it to see if it would boot to XP, but it just flashes something quickly (I think I saw something about GRUB stage2), then goes back to the GRUb menu.

---

### Post by Johan! on 2006-09-15
This is my output of sudo fdisk
```
   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       23516   188892238+   7  HPFS/NTFS
/dev/hda2           23517       24735     9791617+  83  Linux
/dev/hda3           24736       24792      457852+   5  Extended
/dev/hda5           24736       24792      457821   82  Linux swap / Solaris
```

And this is the code in menu.lst
```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

Maybe this helps to create an entry for XP in your menu.lst?

The "root (hdx,x)" refers to the harddrive and partition to boot, in this case the first partition on the first drive. Change it if your setup is different.

---

### Post by sprinkles on 2006-09-15
```
Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63   109772144    54886041    7  HPFS/NTFS
/dev/hda2       109772145   116840744     3534300   83  Linux
/dev/hda3       116840745   117226304      192780    5  Extended
/dev/hda5       116840808   117226304      192748+  82  Linux swap / Solaris

```
That's the output from fdisk, and this was hwat was in menu.lst
```

title		Microsoft Windows 2000 Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

Aside from the name, shouldn't this be working?

---

### Post by Johan! on 2006-09-15
Change root (hdx,x) to rootnoverify (dhx,x)
Remove the savedefault line, or comment it (put a # before the line)
Also, make sure that the devices mentioned in  /boot/grub/device.map are OK

If that doesn't work, then I don't know how to solve it...

---

### Post by sprinkles on 2006-09-16
I'm now getting Error 18 whilst trying to boot Windows :(

edit: I just looked in GParted, and for some reason my Windows partition has a boot flag - is it hosed? :( 

Can I get my data off the drive if I need to re-install?

---

### Post by Johan! on 2006-09-16
[http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)

---

