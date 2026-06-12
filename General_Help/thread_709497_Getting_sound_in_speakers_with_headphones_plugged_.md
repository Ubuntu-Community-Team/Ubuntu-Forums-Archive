---
title: "Getting sound in speakers with headphones plugged in"
date: 2008-02-27
forum: General Help
---

### Post by TE7 on 2008-02-27
Tried many suggestions in the forums. None work. I dual boot with Windows XP and it works fine there, so I don't think it is a hardware problem. While trying to install media programs and get them to work, I upgraded the kernel and other programs and libraries in the process. I've had the problem ever since. Should I try to upgrade to the Hardy in development, or is there a way to undo my changes. Any suggestions are welcome. Thanks in advance for any help.

Running Gutsy in dual boot with Windows XP
Dell Dimension 8400
3 Ghz 1G ram
Soundblaster Live 24 bit sound card

---

### Post by jeffus_il on 2008-02-27
Did you upgrade from the repository or from a manual download? You could install an older kernel from the repository and choose it from the grub menu. Maybe your previous kernel is still install and you can boot from it. It's not a good idea to try Hardy. It should be much easier to fix your problem.

---

### Post by TE7 on 2008-02-27
How exactly do istall my original kernel? I'm tech savvy but new at Ubuntu.

---

### Post by Cris(c) on 2008-02-27
I have exactly the same problem...I've tried pretty much all suggestions I've found on the net but none works....to use only headphones I have to mute the speakers (in the volume control panel) which is a little bit annoying...any new suggestion to solve this problem? I am using Ubuntu 7.10  on a AMD64 machine...

---

### Post by TE7 on 2008-02-28
My mute switch doesn't even work. Anybody got any suggestions on how to make the mute work? That would be an acceptable solution.

---

### Post by Cris(c) on 2008-04-29
It seems that the kernel kernel 2.6.24-16 solves the problem...at least it did it for me. However, it brings some new issues for some people...see [http://ubuntuforums.org/showthread.php?t=768684](http://ubuntuforums.org/showthread.php?t=768684)

---

