---
title: "serious issue"
date: 2007-12-21
forum: General Help
---

### Post by daweefolk on 2007-12-21
i recently installed ubuntu as a second partition on my laptop but somehow the linux partition went corrupt and now I can't use my computer at all. When the computer's booting up, it tries going to the screen where i'd pick between ubuntu and windows but since it's corrupt that screen doesn't even load. is there a way to get around that and simply boot directly into windows?

---

### Post by dlegend on 2007-12-21
Try following this tutorial: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

For it, you'll need the live Ubuntu CD. I'm pretty sure this will help you with your problem.

Also, if you have Windows XP installed on your machine and want it as an option in the GRUB follow this tutorial: [http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp](http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp)

---

### Post by daweefolk on 2007-12-21
i got it to work. i popped the vista install cd in, ran the command line, and typed in
bootrec/fixboot
and
bootrec/fixmbr

and now i booted directly into windows.

---

