---
title: "Can't install Ubuntu 13.04"
date: 2013-07-11
forum: General Help
---

### Post by LywinTannister on 2013-07-11
Hello everyone. I've recently started using ubuntu at work, and as such, have decided to install it as part of a dual boot with windows 7 on my laptop. My laptop is a HP pavilion dv6-3065ea. I've been attempting to install ubuntu from my flash drive, but the problem I'm encountering is that ubuntu doesn't actually install. After proceeding from the first menu (where I chose to Install Ubuntu) I get nothing but a black screen. I've researched this a bit, and a lot of people seemed to have had the same problem. It seems to be happening because of the switchable graphics in my laptop. My laptop has an amd radeon 5470. The most common solution that I've found is to enable "nomodeset[FONT=UbuntuRegular, Ubuntu, Bitstream Vera Sans, DejaVu Sans, Tahoma, sans-serif][COLOR=#333333]**"  **before installing, but I've tried this a few times, and the problem persists. It boots into a black screen. I don't really know what to do from here, so if anyone can help me out I'd be very grateful! :)[/COLOR][/FONT]

---

### Post by fantab on 2013-07-11
You read the following Links..
[https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics)
[http://askubuntu.com/questions/205112/how-do-i-get-amd-intel-hybrid-graphics-drivers-to-work](http://askubuntu.com/questions/205112/how-do-i-get-amd-intel-hybrid-graphics-drivers-to-work)
[http://askubuntu.com/questions/202857/cant-install-ati-proprietary-drivers-in-12-10](http://askubuntu.com/questions/202857/cant-install-ati-proprietary-drivers-in-12-10)

Good Luck...

---

### Post by LywinTannister on 2013-07-11
> **fantab said:**
> You read the following Links..
[https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics)
[http://askubuntu.com/questions/205112/how-do-i-get-amd-intel-hybrid-graphics-drivers-to-work](http://askubuntu.com/questions/205112/how-do-i-get-amd-intel-hybrid-graphics-drivers-to-work)
[http://askubuntu.com/questions/202857/cant-install-ati-proprietary-drivers-in-12-10](http://askubuntu.com/questions/202857/cant-install-ati-proprietary-drivers-in-12-10)

Good Luck...

Thanks for the reply!
Those links don't seem to apply to my situation, I still can't even get ubuntu to install. Straight after the options menu, it loads into a black screen. I can't do anything. This happens even when I use nomodeset.

---

### Post by Yuppa on 2013-07-15
I have the same problem, it both happens with Ubuntu 13.04 64bit and 12.04.2 64bit. I tried secureboot off, nomodeset, Noapic, nolapic but it all didn't help. When I get into grub I click start live or install, it just turns on a dark screen with a blinking _ in the top left corner and then it reboots.  I have Windows7 64bit installed (which runs fine).

---

### Post by mastablasta on 2013-07-15
what abotu minimal install, install AMD drivers and then install the desktop.

---

### Post by Yuppa on 2013-07-15
How can I do that? With the Wubi installer? And what AMD drivers I should install?

---

