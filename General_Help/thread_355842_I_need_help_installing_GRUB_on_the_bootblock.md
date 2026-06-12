---
title: "I need help installing GRUB on the bootblock"
date: 2007-02-07
forum: General Help
---

### Post by waterbear on 2007-02-07
Okay, I just installed NetBSD, and I'm using its boot selector (I like it better than GRUB), but it seems Ubuntu installs GRUB's stage1 in the MBR. Is there any way to put it on /dev/hda?

---

### Post by Maestro23 on 2007-02-07
> **waterbear said:**
> Okay, I just installed NetBSD, and I'm using its boot selector (I like it better than GRUB), but it seems Ubuntu installs GRUB's stage1 in the MBR. Is there any way to put it on /dev/hda?

Might help: [http://www.ubuntuforums.org/showthread.php?t=354059&highlight=grub+on+%2Fdev%2Fhda](http://www.ubuntuforums.org/showthread.php?t=354059&highlight=grub+on+%2Fdev%2Fhda)

---

### Post by waterbear on 2007-02-07
`sudo grub-install /dev/hda1` claims "Could not find device for /boot: Not found or not a block device."

I'm using the 6.06 CD, FYI.

EDIT: However, [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) was a superior set of instructions.

---

