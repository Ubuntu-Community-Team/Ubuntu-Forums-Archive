---
title: "Firefox Graphics Issue"
date: 2024-04-24
forum: General Help
---

### Post by rdege on 2024-04-24
Hello,

I recently installed Xubuntu 22.04 on a new PC Build.  The PC is using the onboard GPU from an AMD 7900 X3D CPU.  Everything displays correctly on the system, except for Firefox (see pic).  Even though you can't see the window, I am able to navigate to websites, and close down the program correctly.

I tried making changes making changes to the Window Manager settings, Display, and XFCE settings with no success.
I also erased the disk and installed ubuntu 23.10 Desktop on the PC, but that suffers from the same issue.

Does anyone know what could be causing it, and how I can fix it?

Thank you

-Robert

---

### Post by coffeecat on 2024-04-25
Support, not chat. *Thread moved to **General Help**.*

---

### Post by hong-xu on 2024-04-29
Have you tried 24.04?

It feels like a graphics driver issue, because Firefox renders webpages and uses more advanced graphics programming interfaces.

If you visit about:support in Firefox, you can see a section called "Graphics". Maybe we can figure out some leads on why things are abnormal from that section if you can post it.

---

### Post by &amp;KyT$0P# on 2024-04-29
Have you tried [disabling hardware acceleration in Firefox]("https://support.mozilla.org/kb/troubleshoot-extensions-themes-to-fix-problems#w_turn-off-hardware-acceleration")?

---

### Post by gezzer2 on 2024-04-29
have a look at this it may help rendering within firefox. if you are familiar with about:config .

 [https://www.ghacks.net/2020/12/14/how-to-find-out-if-webrender-is-enabled-in-firefox-and-how-to-enable-it-if-it-is-not/](https://www.ghacks.net/2020/12/14/how-to-find-out-if-webrender-is-enabled-in-firefox-and-how-to-enable-it-if-it-is-not/)

---

### Post by alextopic on 2024-05-31
[COLOR=#000000]Xubuntu 22.04 might be your problem since it has an older Linux Kernel version like 6.1?
 Well I have a Ryzen 7 7800x3d and RADEON 7800xt graphics and you need a new Linux Kernel version 6.3 and up I believe.
With Ubuntu 24.04 you get Kernel 6.8 so it should help possibly with your problem.
Another problem is make sure your Firefox browser flags for PREFFERED OZONE Platform is set to WAYLAND, just figued that
with Google Chrome they have it set to Xwayland by default but I set it to WAYLAND and works a lot better, so smooth.

[/COLOR]

---

