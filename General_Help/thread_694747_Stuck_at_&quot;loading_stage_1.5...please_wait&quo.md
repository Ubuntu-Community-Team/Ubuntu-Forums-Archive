---
title: "Stuck at &quot;loading stage 1.5...please wait&quot; message. At a complete loss."
date: 2008-02-12
forum: General Help
---

### Post by recursion on 2008-02-12
So, I tried booting my (primary) machine this morning, and instead of being greeted with the login screen, it hung on the message that says something to the effect of "Loading stage 1.5. Loading, please wait..." (there could be more, but my screen has always cut this message off). I left it there, thinking it would eventually finish loading, but it has been stuck for almost an hour. Why?

Is there any command I can do at this screen that would force it to check for errors? What could be causing this? I have no idea what could be wrong, since everything was working fine last night when I shut it down --- I'd experienced no problems whatsoever for months.

---

### Post by buntu_Geek on 2008-02-12
This is BootLoader error...

This means the while loading OS to the main memory there is some problem the bootloader that does this (either GRUB or Lilo..)

You can solve by installing the bootloader again using a ubuntu live CD ...

You can also use another bootloader Super Grub....

btw check this thread.... for the steps for reinstallation of the GRUB,...

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by recursion on 2008-02-12
**Stupid Question:** Can I use a live CD from Feisty to do that if my machine's install was Gutsy? 

To be on the safe side I should just download the 7.10 live CD, right? If I don't have to, though, let me know.

---

