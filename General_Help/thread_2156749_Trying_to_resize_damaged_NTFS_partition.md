---
title: "Trying to resize damaged NTFS partition"
date: 2013-06-22
forum: General Help
---

### Post by hyperkraz on 2013-06-22
Hi guys, I'm new to linux and I am currently trying to resize my old windows partition so I can format the unused space to ext4, but the partition has errors so it asking that I do a chkdsk /f, but my windows 8 is no longer working (hence my using linux...), and although I know I could probably find some bootable usb command prompt in order to do this (like hiren's) I was told I might be able to get this taken care of all through linux...


I stumbled across this other forum [http://www.pclinuxos.com/forum/index.php?topic=95002.0](http://www.pclinuxos.com/forum/index.php?topic=95002.0) and saw this thread, To get to the point:

When I try to use "ntfs-3g -o recover /dev/sda4" it says "no mountpoint specified"

BUT when I mount it to say, /mnt/windows, and try running "ntfs-3g -o recover /dev/sda4 /mnt/windows" it then tells me that "the mount is denied because the NTFS volume is already exclusively opened"


SO it seems that it cannot run without a mountpoint specified, but when I mount it, it becomes unusable.

So can someone please, please tell me what's going on here because Terminal is just contradicting itself.

---

### Post by oldfred on 2013-06-23
Generally the Linux NTFS driver will not mount a NTFS partition with the chkdsk flag set nor with hibernation file set. 
Always best to run chkdsk from Windows and resize Windows 7 or Windows 8 from inside the Windows install using its Disk tools. 
After a resize NTFS always needs a chkdsk.

---

### Post by Impavidus on 2013-06-23
Linux cannot repair that ntfs partition (not reliably at least). If you want to repair and resize it, first repair and then resize, both from windows. If there's no valuable data on it and you just want to get Linux installed, you can use gparted to delete the ntfs partition and create a new Linux partition (and possibly a new ntfs partition for reinstalling windows), but this will destroy all data on the ntfs partition.

---

