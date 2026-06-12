---
title: "Why almost every Windows update needs a reboot? Why is Linux different?"
date: 2007-08-04
forum: General Help
---

### Post by benton on 2007-08-04
Hi there, 

As all you know, nearly all windows automatic updates need to reboot the OS. I've noticed that while Ubuntu gets more automatic updates in a month than Windows does, a reboot is rarely needed. I'm curious about this difference so... anyone please care to explain?

Regards,

-Benton

---

### Post by w4ett on 2007-08-04
The reboot in Windows is due to the use of a registry in the NT kernel (yes windows has a kernel, but it is hidden from the user).....since linux has no registry, only kernel related updates require a reboot.

---

### Post by benton on 2007-08-04
Interesting... thanks. I thought it was because the files were in use so a reboot was in order and I though Linux was handling "in use" files a bit different maybe and that would be why it didn't need to reboot as much as Windows.

So then basically Windows and Linux handle "in use" files in the same way and updating those files would require a reboot and both OSes?

Regards,

-Benton

---

### Post by eentonig on 2007-08-04
No, because in general, 'in use' files, will only require a reset of the process in question. As said, the only reason you'll need a reboot, is if the kernel itself is being updated. But the kernel is the very core of your system. And usually, it doesn't get updated unnecessarely.

---

### Post by HermanAB on 2007-08-04
Linux is more modular than Windows.  Therefore you can update a specific module and then only restart that single module to run the new code.  However, if you upgrade the Linux kernel which is central to everything, then you do need to restart the whole thing.

Windows is more like a house of cards - remove one card and the whole damn thing collapses.

---

### Post by Nythain on 2007-08-04
and then there's the fact that most of the damn updates in microsoft dont even really REQUIRE an effen reboot, they just want you to, to be annoying punks :)

---

