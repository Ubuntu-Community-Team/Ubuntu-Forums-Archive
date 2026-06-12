---
title: "Windows doesn't like dual boot"
date: 2015-08-04
forum: General Help
---

### Post by tony87 on 2015-08-04
I boot into windows to play video games and after I set up Ubuntu, windows doesn't recognize any USB devices so I can't log in with my keyboard. When the loading screen comes up, the devices used to turn off and then back on. Now they turn off and never come back on. Please help.

---

### Post by Vladlenin5000 on 2015-08-04
Hi and welcome.

Dual boot has nothing to do with it and by "it" I mean whatever you (think) you're experiencing but couldn't describe properly. Please give more details.

---

### Post by ruzekle on 2015-08-04
I had a similar issue with an older computer using Xubuntu. What had happened was the most recent kernel update had caused compatibility problems. That sometimes happens. When your computer boots, use an older kernel version (use the down arrow key).

[IMG]https://upload.wikimedia.org/wikipedia/commons/1/12/GRUB_screenshot.png[/IMG]

---

### Post by Vladlenin5000 on 2015-08-04
@ruzekle - Perhaps you should read the OP again... Namely that part about
> (...) _windows_ doesn't recognize any USB devices so I can't log in with my keyboard. (...)
hinting that it is something somehow related to having Ubuntu installed in dual boot.

---

### Post by ruzekle on 2015-08-04
> **Vladlenin5000 said:**
> . . . somehow related to having Ubuntu installed in dual boot.

Ah, I see. I don't see how this could be the case. My next suspicion is either there's a hardware or drivers issue. If it's only Windows, then that should suggest that there's a Windows driver issue. If that's the case, I think going to Microsoft for support may be a better course of action than asking Ubuntu's community.

---

### Post by Vladlenin5000 on 2015-08-04
Some UEFI/BIOS change along with the boot settings for the installation it's also plausible but, again, nothi8ng to do with the dual boot *per se*. The inference in the thread title and the whole description still doesn't make sense though.

---

### Post by leunam12 on 2015-08-05
It sounds like there was a change in the BIOS. Can you access the BIOS? see if there is a section that allows to enable and disable a USB keyboard.

---

### Post by monkeybrain20122 on 2015-08-05
> **ruzekle said:**
> I had a similar issue with an older computer using Xubuntu. What had happened was the most recent kernel update had caused compatibility problems. That sometimes happens. When your computer boots, use an older kernel version (use the down arrow key).

[IMG]https://upload.wikimedia.org/wikipedia/commons/1/12/GRUB_screenshot.png[/IMG]

Ubuntu 8.04??!! I hope this is not a current screenshot. BTW the bootscreen doesn't look like this in current Ubtuntu, it only show the most recent kernel, to access others you need to click "advanced options" or something like that.

---

