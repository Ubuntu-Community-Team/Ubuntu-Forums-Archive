---
title: "Mounting Issues"
date: 2007-01-25
forum: General Help
---

### Post by Happy_Man on 2007-01-25
Hi everyone!

I have a dual-boot setup w/Feisty and XP, so far everything's fine, no problems! Except that it keeps switching which partition it automounts on boot. Here's my fdisk:

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1           5       40131   de  Dell Utility
/dev/hda2   *           6        9158    73521472+   7  HPFS/NTFS
/dev/hda3            9159       14500    42909615   83  Linux
/dev/hda4           14501       14593      747022+   5  Extended
/dev/hda5           14501       14593      746991   82  Linux swap / Solaris

Either it mounts /dev/hda1 or /dev/hda2 on the desktop at boot. It's totally random which one. Whatever it does display, though, I can still access my windows files through /media, so it's not like I'm totally cut off. Is there any way I can prevent /dev/hda1 from ever loading up? I don't really need it...

---

### Post by benerivo on 2007-01-25
Have you tried looking at your fstab file, and removing the /dev/hda1 entry line? From here you can also control what mounts and whereabouts.

---

