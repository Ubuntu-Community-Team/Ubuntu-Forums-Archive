---
title: "&quot;Missing operating system&quot; error on boot up."
date: 2007-01-13
forum: General Help
---

### Post by LPomfrey on 2007-01-13
I've recently moved my /home to another hard drive. When I rebooted I couldn't log in because I'd screwed up fstab, so I fixed (I think) that using a Live CD. Now whenever I reboot I'm getting a "Missing operating system" error. 

I've tried this method to reinstall grub,  [http://doc.gwos.org/index.php/Restore_Grub](http://doc.gwos.org/index.php/Restore_Grub) but it won't let me continue past the partition stage without formatting, which I obviously do not want to do. I've also tried:
```
sudo grub-install --recheck --no-floppy /dev/hdb3
```

But that fails saying:

```
Could not find device for /boot: Not found or not a block device.
```

If anyone has any suggestions that would be great.

---

### Post by meng on 2007-01-13
You should probably tell us your hard disk and partition setup at present. It looks like you are trying to install grub to /dev/hdb3, i.e. not the MBR of the drive, which is fine IF you have another bootloader on the MBR, but it appears that you don't, which is why you get the missing OS message.

---

### Post by LPomfrey on 2007-01-13
I've got:

```
/dev/hda1 mounted as /home
/dev/hdb1                   swap
/dev/hdb2                   not mounted
/dev/hdb3                   /              (where Grub was before this.)
```

---

### Post by meng on 2007-01-13
Are you certain grub was on /hdb3, because it's more likely to have been installed to the MBR. That's where your system will automatically look for a bootloader to start with. My suggestion is to install grub to /dev/hda (no number!!!!)

---

### Post by LPomfrey on 2007-01-13
> **meng said:**
> Are you certain grub was on /hdb3, because it's more likely to have been installed to the MBR. That's where your system will automatically look for a bootloader to start with. My suggestion is to install grub to /dev/hda (no number!!!!)

Thanks, it installed (apparently), hopefully it'll boot properly now. 
I was obviously completely missing the point about where it would be installed. :-?  *goes to read GRUB documentation*

EDIT: Yea, it works. Thanks a lot. :D

---

