---
title: "Laptop Screen Flickering After Locking Screen"
date: 2022-01-23
forum: General Help
---

### Post by arminius-superbus on 2022-01-23
Hi @all

A really strange problem occured a while ago on my Lenovo T14 running Ubuntu 20.04.3 LTS 64-Bit (Gnome Version 3.36.8, Windowing System: X11, Processor: AMD® Ryzen 7 pro 4750u with radeon graphics × 16, Using Disk Encryption). I have no pending software updates and everything should be up to date.

**The problem:**

Whenever I lock the screen (Windows-Key + L) and try to unlock again after a few seconds, the screen of the laptop is just showing flickering and white noise as shown in the attached screenshot.
What's interesting, however, is that when I attach a second monitor, everything is working fine on that monitor. Just the laptop screen says goodbye after locking the operating system. This is especially annoying, if you are on the road and have no second monitor at hand. In that case you cannot lock the screen, otherwise you cannot log back in and have to shut down the computer first.

I do NOT think that this is a hardware problem for the following two reasons:

1) The laptop screen is working perfectly fine as long as I do not lock the screen. It runs for hours without flickering and also shaking the laptop does not cause problems. So it cannot be a lose wire or something like that.
2) A colleague of mine has exactly the same laptop as me, running the same version of Ubuntu and the problem started appearing on his computer at exactly the same time as for me (4 days ago). His flickering screen also look exactly like mine in the screenshot. Even with the same vertical stripe pattern on the right side of it and random white noise everywhere else.

I hope you can help me, it is really annoying and I have been using this setup happily for over a year now.


[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289887&stc=1[/IMG]

Thanks a lot!

---

### Post by mapniv on 2022-01-28
This is a known problem with Linux kernel 5.13.0. Try using older kernel. To do so press escape or shift during boot depending on whether you use UEFI or BIOS respectively. A menu should appear. Choose 'Advanced options for Ubuntu' and then 'Ubuntu, with Linux 5.11.0-46-generic'. There is an option to make it permanent. See post #15 here: [https://bugs.launchpad.net/ubuntu/+source/linux-hwe-5.13/+bug/1958591](https://bugs.launchpad.net/ubuntu/+source/linux-hwe-5.13/+bug/1958591).

---

