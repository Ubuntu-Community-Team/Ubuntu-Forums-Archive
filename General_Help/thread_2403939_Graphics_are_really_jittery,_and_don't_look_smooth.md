---
title: "Graphics are really jittery, and don't look smooth"
date: 2018-10-18
forum: General Help
---

### Post by greda2 on 2018-10-18
Just installed Ubuntu and done regular updates and whatnot. Coming from Windows 10, everything from opening up an application, to dragging a window, or unlocking my computer are really jittery. Is there any way to make things look smooth? Using Intel HD 630 Graphics if that helps.

---

### Post by HermanAB on 2018-10-18
The origin of the problem is that you have a bad video display driver installed.  How exactly to fix it, depends on which display card/chipset you are using.  Some googling should eventually get you going.

However, the trouble with fixing a display driver, is that you may end up with a black screen, which can be very hard to fix, since then, you cannot see what you are doing.  Therefore, first make a backup of all your data, in case you need to re-install.  Then enable the ssh daemon, so that you can log in remotely over ethernet from another computer, when your computer screen went black.

Unless you have much Linux experience, it may be easier to install a different Linux distribution, such as Mint, Fedora, PCLinuxOS, Debian, Arch, Gentoo...  Chances are that one of them will install and work perfectly on your hardware without you having to jump through any hoops.

---

### Post by mrdc76 on 2018-10-18
> **greda2 said:**
> Just installed Ubuntu and done regular updates and whatnot. Coming from Windows 10, everything from opening up an application, to dragging a window, or unlocking my computer are really jittery. Is there any way to make things look smooth? Using Intel HD 630 Graphics if that helps.

No, I am afraid there is not. Mine is just the same, and has been for a few releases. I also have Intel graphics. I presume the main culprit is Gnome, which did get some speed related bug fixes for the 3.30 release, but those won't be available to Ubuntu 18.04. Trying a different desktop environment (i.e., a different release of Ubuntu) might help.

---

