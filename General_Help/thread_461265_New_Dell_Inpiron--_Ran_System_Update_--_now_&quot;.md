---
title: "New Dell Inpiron-- Ran System Update -- now &quot;Cannot Mount Selected Partition&quot;"
date: 2007-06-01
forum: General Help
---

### Post by sibir on 2007-06-01
I just got my new Dell Inspiron w/ Ubuntu about an hour ago. First I ran apt-get update and upgrade. I then saw the system update icon pop up, so I ran that. It updated the kernel image.  It suggests a reboot, which I allow. Upon bootup, I get this:

Error 17: Cannot mount selected partition

Press any key to continue...


then I get  a choice between:

Ubuntu, kernal 2.6.20-16-generic
Ubuntu, kernal 2.6.20-16-generic (recovery mode)
Ubuntu, kernal 2.6.20-15-generic
Ubuntu, kernal 2.6.20-16-generic (recovery mode)
Ubuntu, memtest86+
Reinstall Operating System (WARNING: all Hard Drive data will be LOST->


For each of the first 4 choices, I get the same cannout mount error. I haven't yet tried the reinstall operating system option...   Any suggestions? I'll do the reinstall, but I'd really like to be able to stay current wrt the kernel...

---

### Post by confused57 on 2007-06-01
You might want to read this:
[http://ubuntuforums.org/showthread.php?t=453741&page=4](http://ubuntuforums.org/showthread.php?t=453741&page=4)

---

### Post by awkwardmoment on 2007-06-01
You might try this tutorial to restore grub [http://ubuntuforums.org/showthread.php?t=224351&highlight=restore+grub]("http://ubuntuforums.org/showthread.php?t=224351&highlight=restore+grub")
It saved me from reinstalling ubuntu after I installed xp.

---

### Post by sibir on 2007-06-01
> **awkwardmoment said:**
> You might try this tutorial to restore grub [http://ubuntuforums.org/showthread.php?t=224351&highlight=restore+grub]("http://ubuntuforums.org/showthread.php?t=224351&highlight=restore+grub")
It saved me from reinstalling ubuntu after I installed xp.

Thanks for that. I tried to reconfigure grub, but I couldn't find anything. I tried setting root (hda, 2), but I couldn't get anywhere. I'm a noob at grub. I'm just reinstalling to the factory default.

---

### Post by sibir on 2007-06-01
> **confused57 said:**
> You might want to read this:
[http://ubuntuforums.org/showthread.php?t=453741&page=4](http://ubuntuforums.org/showthread.php?t=453741&page=4)

Thanks, that's exactly what I needed.

---

