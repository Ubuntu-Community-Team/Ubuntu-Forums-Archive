---
title: "Can't startup OS! usb 2-5: device descriptor read/64, error -110"
date: 2016-05-10
forum: General Help
---

### Post by neu5eeCh on 2016-05-10
Why am I even getting this error message? I'm booting from my SSD like I have for years?!? 

So, I'm writing this on my tablet. Can't use my laptop.  :-/

---

### Post by neu5eeCh on 2016-05-10
Also, I can use tty and access my hd. Its the startup thats the problem.

**Edit: **Okay**... _Blimey!_** I've been having all sorts of problems with Kernel 4.4. For a while, I began booting with kernel 4.2. Then today, at the coop, my panel was flickering badly. I tried this:  

[https://www.kubuntuforums.net/showthread.php?69984-FIX-for-flickering-flashing-panel-on-Intel-gpu](https://www.kubuntuforums.net/showthread.php?69984-FIX-for-flickering-flashing-panel-on-Intel-gpu)

> TESTED ON KUBUNTU 16.04 LTS

If you experience flickering/flashing panel in plasma 5 with intel graphics, follow this tutorial to fix it.

Fix/workaround is to use DRI3 instead of default DRI2. DRI3 works great for me and fixes few problems/bugs that I experience with intel gpu driver.

1) Press alt+f2 and type
Code:

kdesudo dolphin

2) Navigate to /root/etc/X11/xorg.conf.d folder.

If xorg.conf.d folder does not exist, create it (right mouse click>create new>folder)

3) In xorg.conf.d folder create text file 20-intel.conf (right mouse click>create new>text file)

4) Open 20-intel.conf text file and add this content:
Code:

Section "Device"
    Identifier  "Intel Graphics"
    Driver      "intel"
    Option      "DRI"    "3"
EndSection

save and exit.

And then I started getting that USB error. Trying different kernels, I got a blank screen; then I remembered that I had installed the Intel Graphics Drivers. So, using TTY, I removed the 20-intel.conf file that I had created. I'm back. What a mess! I'm currently using 4.4.0-18-generic. Hopefully my TTY's will continue to function (which is why I switched to 4.2). I think I might need to upgrade to 4.6.

---

