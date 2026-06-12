---
title: "Boot Error, No HD found"
date: 2007-04-02
forum: General Help
---

### Post by theRevMom on 2007-04-02
I've been running Edgy for a couple of weeks without any boot issues... until today. I tried to reboot the system.  It got to BIOS and came up with an error that it could not find HD0.  I've only got one.  Hmm.  So I went into Bios Setup and double checked the boot order etc. BIOS had no HD listed.  I changed nothing (tho contemplated adding a USB to the boot order).  The system restarted and again, no HD0.  It gave me a choice of F2 for setup or F1 to continue.  I chose F1 to see what would happen.

It immediately went into GRUB.  

Okay, so now I'm on. I backed up all my important stuff onto a USB drive.  I was thinking I probably had the bad luck of choosing a bad HD from my salvage heap.

Anyone have an idea here?  Is this a sequence error or do I need to go buy a new HD....

---

### Post by davidgarcin on 2007-04-02
It sounds to me like either GRUB or the Master Boot Record was changed (somehow).  Before ditching the hard drive, I would try reinstalling GRUB, and I would also double-check your /boot/grub/menu.lst to make sure everything's kosher.

Even if you can't boot your Linux partition, you can still access your system by booting from the Live CD.  Here's a thread with instruction for reinstalling GRUB (there are lots):

[http://ubuntuforums.org/showthread.php?t=358183&highlight=windows](http://ubuntuforums.org/showthread.php?t=358183&highlight=windows)

It's right near the top.

---

### Post by davidgarcin on 2007-04-02
actually, this is a better guide for reinstalling GRUB.  I've used it before, and it worked well:

[http://www.ubuntuforums.org/showthread.php?t=224351&highlight=installed+windows+lost+grub](http://www.ubuntuforums.org/showthread.php?t=224351&highlight=installed+windows+lost+grub)

---

### Post by theRevMom on 2007-04-03
thank you!  I followed the second instructions and the problem is solved.  Mucho Gracias!

---

### Post by davidgarcin on 2007-04-03
Glad I could help.

---

