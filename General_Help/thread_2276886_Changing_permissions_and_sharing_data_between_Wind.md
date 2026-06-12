---
title: "Changing permissions and sharing data between Window$/Ubuntu graphically"
date: 2015-05-05
forum: General Help
---

### Post by isurveilu on 2015-05-05
I have 2 parents who run Ubuntu 14.04 on separate machines with different user names. My sister has a dual boot Windows 7/8 machine and they share data between themselves with 8-32 GB USB sticks. They don't want a NAS, network or cloud solution. They also share files with friend who also have Windows PCs this way.

The solution I need has to be stupid simple and graphical. I also admit to a lack of understanding of Linux permissions. I've tried on my own rigs (Ubuntu 14.04 another with with Windows 7) sharing data between Linux and Windows machines, [http://ubuntuforums.org/showthread.php?t=2276172](http://ubuntuforums.org/showthread.php?t=2276172)

I can change the permissions in Nautilus as root so anyone can read/write/modify but the permissions get rolled back so only root can after the USB stick is used on another machine, whether Windows or Linux.

Basically, there needs to be no involvement with the terminal. All 3 need to be able to read/write to the same USB sticks with no involvement from me as far as setting up/maintaining. I've tried:

1. The default EXFAT file system. With a new USB stick, reading and writing in Linux in the first machine isn't an issue, But as soon as it's used in another machine only root can write to it.

2. NTFS Can't write to it at all in Linux, even when setting ntfs-config to write, unless root.

3 EXT4 with the Paragon Drivers for Windows [http://www.paragon-drivers.com/extfs-windows/](http://www.paragon-drivers.com/extfs-windows/) Same as 1.



TL;DR

1. Is there a simple graphical utility to set permissions permanently so ALL users can read/write/modify the USB drives? Nautilus isn't cutting it and I have to open it as root in the terminal. A no-go for my parents.

2. best file system? (probably EXFAT, but by all I've read it doesn't seem to be well supported)

3. Why do my permissions keep getting rolled back so only root can write to these drives?

By the way, My Ubuntu machine that I've been testing the sticks on the most is LUKS encrypted. Any chance there's something with the permissions? can't seem to find one. I want to try this on my stuff first since they all live pretty far away.

---

### Post by Mark Phelps on 2015-05-05
I use USB sticks to migrate files between Win8 and Linux distros all the time -- and I never encounter a permission problem.  But then, I didn't mess around with the permissions when I formatted the USB sticks -- and I did that in Windows, not in Linux.

When I insert the USB stick, a window opens showing the contents of the stick (in Nautilus) and I can read/write without problems.

Suggest you try reformatting a USB stick to NTFS in Windows -- and see if that works in the Linux distros without having to tweak permissions.

---

### Post by ajgreeny on 2015-05-05
If a USB drive is formatted to either fat32 or NTFS you should be able to read and write to it in a default *ubuntu OS, but you should remove **ntfs-config** as I believe it can conflict with** ntfs-3g** which should be all that is needed to read/write to NTFS provided you have always removed the USB properly from any Windows OS; if you don't remove it properly it will still be seen as "in use" and impossible to mount or use in Linux.

I would suspect that maybe your parents or sister are just pulling the USBs out of machines without removing them properly, ie unmounting them, in Linux speak, by using the icon in the Windows panel, bottom right (that's where it was in XP; no idea about later Windows versions as I haven't used them) and doing that will cause all sorts of difficulties.

---

