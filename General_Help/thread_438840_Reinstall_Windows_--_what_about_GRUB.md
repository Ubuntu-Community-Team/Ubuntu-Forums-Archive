---
title: "Reinstall Windows -- what about GRUB?"
date: 2007-05-10
forum: General Help
---

### Post by Znupi on 2007-05-10
Ok, so... I want to format my Windows partition (J:\, lol) and reinstall it. I want to use it JUST for gaming. All the rest I can do on Ubuntu. BUT, I know that I won't be able to start Linux anymore, because Windows will take over GRUB. How can I change it back? Can I install grub from Windows? Or maybe using the Ubuntu Live CD?...

---

### Post by rai4shu2 on 2007-05-10
I suggest this:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Znupi on 2007-05-10
> **rai4shu2 said:**
> I suggest this:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
Thanks, but how do I know which one of those two methods I should follow? The first one seems easier, but what does "Preserving the Windows bootloader" mean? Sorry, I'm a bit noobish... :oops:

---

### Post by orb9220 on 2007-05-10
> but what does "Preserving the Windows bootloader" mean?

Which you don't need to do since the windows bootloader is the mbr which you will be overwritten with grub.
[http://www.ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub](http://www.ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub)

---

### Post by Znupi on 2007-05-10
So I have to go for the second method? Wouldn't it be easier to use the [Super Grub Disk](http://supergrub.forjamari.linex.org/)? It seems nice and easy to use...

---

### Post by strabes on 2007-05-10
Use the method that you feel the most comfortable with. If that's the super grub CD, it will cost you a blank CD-R, but it should be pretty easy.

---

