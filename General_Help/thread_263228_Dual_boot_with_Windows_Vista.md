---
title: "Dual boot with Windows Vista"
date: 2006-09-22
forum: General Help
---

### Post by Christopher999999 on 2006-09-22
I used to use Ubuntu but then switched to Windows Vista. Now I decided to install Ubuntu over my Windows XP installation. I thought that the install process would automatily insert Windows Vista into the boot screen. It did not and now I can only get into Ubuntu and not Vista. Vista is installed on the slave drive. Does anyone know how to get Windows Vista to boot? Vista did show me a screen before I installed Ubuntu asking me if I want to boot into XP or Vista. Thanks!

Edit: I know that my disk is hd1,0
Booting to that will cause my computer to reboot.
I have it set up to boot like this:
title           Microsoft Windows
root            (hd1,0)
savedefault
makeactive
chainloader    +1

Is this a problem with my configuration of the boot loader or is at a prolem with Windows?

---

### Post by Opsidian on 2006-09-25
let me know if you figure this out, I screwed up and decided to test Vista on the laptop and now I'm either able to boot on or the other depending on the last installed.

---

### Post by Christopher999999 on 2006-09-25
I was told on the Vista Support Group, that when I installed Ubuntu over XP, the boot files for Vista were deleted also as they were on the master drive which I installed Linux on.

---

### Post by testube_babies on 2006-09-25
maybe some info in this dual-boot howto can help you out (it worked for me):

[http://www.ubuntuforums.org/showthread.php?t=207870](http://www.ubuntuforums.org/showthread.php?t=207870)

---

