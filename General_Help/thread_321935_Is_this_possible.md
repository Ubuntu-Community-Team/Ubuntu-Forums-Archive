---
title: "Is this possible?"
date: 2006-12-19
forum: General Help
---

### Post by Origin on 2006-12-19
Is it possible to eliminate the redundancies you get from installing Ubuntu x64_86, Ubuntu x86, Fedora x64_86, x86, etc? They all use the same programs anyway. I want to have the opportunity to select which OS I boot into with GRUB, but I don't want to allocate 10 GB for each of them. I have a 80 GB laptop, half of which I reserve for Windows XP (x86 and x64_86)

Thanks.

By the way, my Broadcom WLAN still isn't working :(

---

### Post by linuchsan on 2006-12-19
no...you can't

---

### Post by enopepsoo on 2006-12-19
> **linuchsan said:**
> no...you can't

You probably could if you wanted to leave the package managing system.  You could install a bunch of stuff (like your programs that you use the most, like firefox etc) into a common /opt folder perhaps!  I am sure that if you want to use apt / rpm etc that this will not work.

Maybe give it a try in a virtual machine and see what happens...](*,)

---

### Post by az on 2006-12-19
No, because they are not binary-compatible.

This software is developped collaboratively and interfaces at the source code level - not the binary level.  To make the code binary-compatible would slow development, increase security vulnerabilities and make the code less efficient.

---

