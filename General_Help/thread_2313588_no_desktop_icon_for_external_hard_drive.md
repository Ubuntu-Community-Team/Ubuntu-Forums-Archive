---
title: "no desktop icon for external hard drive"
date: 2016-02-13
forum: General Help
---

### Post by marsdenf on 2016-02-13
Using xubuntu 14.04 on both a desktop and a laptop.   I have a Seagate 1tb external hdd formatted for FAT32 with a bunch of files on it.   On both computers there is no desktop icon for it when it is plugged in.  To mount the device and access the files I use disk utility and click on /media/marsdenf/EXT_HDD.  Even after mounting there is no icon.  On desktop settings I have "default icons" set to show everything.  Isn't there supposed to be a desktop icon?

---

### Post by coldraven on 2016-02-14
Go to Settings>Removable Drives and Media. Make sure that the "Mount removable drives when hot-plugged"  checkbox is ticked.

---

### Post by marsdenf on 2016-02-14
It was already checked, on both computers

---

### Post by coldraven on 2016-02-14
That's strange! I have tested this with both a 1TB ext. drive (NTFS) and also a 8GB memory stick (FAT32), they both auto-mount (with notification) and appear on the desktop as icons. I'm running Xubuntu 14.04.2 on a netbook. AFAIR this is clean install and I have not meddled with the OS. 
I only occasionally use this netbook and ext.drive. I had to go and find all the wires etc. which is why I did not tell you this in the first place.

Come on Xubuntu users, tell the OP what has happened! :)

---

### Post by speartip on 2016-02-14
Try Settings/Desktop/Icons/Removable Devices.
Something there is probably unticked.

---

### Post by marsdenf on 2016-02-14
As I mentioned in the original post, desktop-icons-default icons,  everything is checked to show up on the desktop

---

### Post by speartip on 2016-02-14
Ok. Above "Default Icons" in the "Icon Type" box, is it set to "file/launcher icons" ?

---

### Post by ajgreeny on 2016-02-14
Is this disk attached but not showing when you boot the machine, or does the disk not mount and show when you plug it in after boot?

If the former, you may need to edit /etc/fstab and add a line to mount it at boot.

I have just attached my external drive (ext4, but that should not matter) and a fat32 memory stick, so will see what happens when I reboot and then I'll report back.

EDIT:
Ok I have rebooted and both disks show on the desktop as icons as I expected, but neither of them are mounted, so you are definitely getting different behaviour to the expected; we simply have to figure out why this is the case.

Can I check that you use thunar as the file-manager and that you have nor removed that and use something else as the default, as that can do strange things to the desktop display and management.

---

### Post by marsdenf on 2016-02-14
Yes, default file manager is thunar.  Also icon type is set to file/launcher icons

---

### Post by marsdenf on 2016-02-14
Yes, default manager is thunar.  And icon types is set to file/launcher icons.   If I plug in the drive after booting up, no icon appears and thunar does not list the drive, but disk utility sees it fine.  After using disks utility to mount the drive,  I can access it at /media/...   and thunar recognizes the drive, but no desktop icon.  I then unmount the drive and reboot the computer with drive still plugged in, and the same thing happens.

---

### Post by Dennis N on 2016-02-14
Maybe you are looking in the wrong place: since you report this happens in two computers, perhaps the drive itself is at fault - perhaps it misidentifies itself as to what type of device it is.

---

### Post by marsdenf on 2016-02-14
Dennis I think you may be right.  When I got the drive it had some windows files on it.  I didn't know what I was doing, and deleted all those files, and then got instructions on how to use the command line to format the drive for FAT32.  Maybe I deleted a necessary file at the beginning.

---

