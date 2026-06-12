---
title: "4K display issues, Ubuntu 14.04 and 15.04"
date: 2015-10-04
forum: General Help
---

### Post by trexgrec on 2015-10-04
Hello all!
I am not new to Ubuntu and Linux, but I do not consider myself to be the super expert either. So I post this issue to "General Help" because I don't know how to categorize it.
I have just bought a new laptop which as a really good 4K display, (3840 x 2160), and Win10 has no issue with it, it works perfectly well. Ubuntu 14.04 however shows everything in a very, really small scale, the menus, bars, programs, intro screen, really everything. The currents drivers successfully reach high resolution, however once I launch any internet browser, (eg Firefox or Chrome) the display starts flickering massively. When I close the browsers, the flickering stops! 

Concerning the small bars, icons, menus etc, I attempted to do "Scale for menu and title bars" on the "Display" menu, the scale worked and the menus and bars show nicely, however the flickering with the browsers when they start, still remains.

I was forced to downgrade the resolution into a standard 1920x1080, and now the flickering has stopped!
So I was wondering to whom am I supposed to report for this issue. Is there a way (currently) for Ubuntu to handle 4K displays in a better way, that means proper scale up off the menus and fonts, no flickering etc? I also tried v 15.04 and I still had the same problems.

Thanks in advance.

---

### Post by mark-wheadon on 2015-10-20
Hello,

I get this too, but only when using Chromium or Chrome. I am using Ubuntu 15.04 (64-bit) and an AMD APU (AMD A10-7800 Radeon R7, 12 Compute Cores 4C+8G × 4 - AMD Radeon(TM) R7 Graphics) with the default driver (not Catalyst). Firefox works fine. If I open Chrome with a small window (about 800x800 at a guess) then it works fine, If I then make the window larger in either width or height then it starts to flash back and forth between the old size and the new. To fix it I have to reduce the size again, close it and open it again (and, in the case of Chrome, exit the notification icon). I did once create a new tab then make it bigger and that was fine, but then could not reproduce this solution. I only have this problem with Chrome/Chromium.

---

### Post by jernej-jerin on 2015-11-20
I have also come across this issue on Ubuntu 15.10, using AMD FirePro W4100. I am using Unity desktop environment, with two monitors acting as a single screen using AMD Eyefinity technology. One monitor is 4K and the other one is QHD. But the flickering does not appear always, I think I have managed to reduce the probability of flickering appearing by setting option for screen tearing under Catalyst Control Center. But when resizing Chrome window I still get flickering. Thinking about trying GNOME 3 desktop environment.

---

### Post by oldfred on 2015-11-20
Do not know if just Intel or others also:
 Have Troubles With 4K Displays On Intel Linux? Try The Linux 4.3 Kernel
[http://www.phoronix.com/scan.php?page=news_item&px=Linux-4K-4.3-Fix](http://www.phoronix.com/scan.php?page=news_item&px=Linux-4K-4.3-Fix)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)
[http://blog.ffwll.ch/2015/09/neat-drmi915-stuff-for-43.html](http://blog.ffwll.ch/2015/09/neat-drmi915-stuff-for-43.html)

---

