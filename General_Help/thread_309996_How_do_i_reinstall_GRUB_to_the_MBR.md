---
title: "How do i reinstall GRUB to the MBR?"
date: 2006-11-30
forum: General Help
---

### Post by jdhore on 2006-11-30
i currently have Windows XP and Ubuntu 6.10 installed on my HD. later this evening, i'd like to install Windows Vista onto this computer (effectively overwriting the XP partition/install), by doing this, i'm pretty sure Vista is going to overwrite the MBR with the Windows Bootloader and i'll be locked out of Ubuntu, my question is, what's the easiest way to get it back (i know i can boot to the live CD and reinstall Ubuntu and it'll put GRUB back, but i'd prefer not to do that if possible.

Thanking you all in advance for you help.
JD

---

### Post by PurplePenguin on 2006-11-30
No, you shouldn't have to go through the trouble of reinstalling Ubuntu!  One of the guys who has been with Ubuntu for longer than I have will reply soon enough, I'm sure, but I'm sure that there's a "rescue" mode on the install CD.  This should allow you to reinstall grub.

EDIT: I found a link that should help you. [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") 
This goes step by step and makes it look quite easy. :)

---

### Post by ajgreeny on 2006-11-30
If your machine still has a floppy, look at:-
[http://ubuntuforums.org/showthread.php?t=269175](http://ubuntuforums.org/showthread.php?t=269175)
which could be useful as well.  It's s shortcut to producing a grub floppy disk which you can then use to boot the computer and then get grub back on the MBR, assuming it's on hda, of course, with *sudo grub-install /dev/hda*

---

