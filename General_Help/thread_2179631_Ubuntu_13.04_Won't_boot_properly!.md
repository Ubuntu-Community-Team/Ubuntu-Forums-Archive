---
title: "Ubuntu 13.04 Won't boot properly!"
date: 2013-10-09
forum: General Help
---

### Post by kyle-sellers2 on 2013-10-09
I installed ubuntu 13.04 yesterday, on my Acer Aspire V3-551G-8454. Ubuntu has been working fine up to this point. When I boot Ubuntu, the screen seems to become offset, and the text lines are split and look like bail. The boot sequence seems to stop, and looks like what is in the picture below. I cannot seem to be able to interact in any way shape or form, short of turning off my computer with the power button. (Before you ask, yes, I can get into the BI/OS)[IMG]http://i.imgur.com/ODuhqBx.jpg?1[/IMG]

---

### Post by heir4c on 2013-10-09
Normally that is a driver issue. Have you installed the non-free driver (before you have this)?

Choose in the Grubmenu the second line (Ubuntu recovery) and when you come in the little menu than choose: failsafeX
There you can solve some problems. 
Or start further to the desktop and switch to the open driver (via Software&Updates) if you have used the non-free driver.
You can look in /var/log/Xorg.0.log file for errors.

---

### Post by kyle-sellers2 on 2013-10-09
When I select the option " Ubuntu, with Linux 3.8.0-31-generic (recovery mode) " a whole bunch of what i believe to be text scrolls by, then this happens to the screen and it stays like this.[IMG]http://i.imgur.com/qUKY7Ij.jpg[/IMG] I seem to be able to input something during this screen. What i believe to be hapening, graphically, is that the boot sequence has misaligned  the screen, and seems to put 1/4 of the screen on both the left and the right.

---

### Post by heir4c on 2013-10-09
What you see on the screen is the little menu.
Try first to start further by pressing just Enter.

---

### Post by kyle-sellers2 on 2013-10-09
Pressing enter bring me to a new menue, and yes I do believe that I installed the official AMD graphical drivers.

---

### Post by heir4c on 2013-10-09
Sorry, Yes he ask confirmation.So click again Enter and now he must be go direct to the log in screen. Log in and if you switch to the non-free switch back to the open source driver and reboot. If all go well than there is a issue with the driver.

---

### Post by kyle-sellers2 on 2013-10-09
When i get to the first menu, i hit enter, and the same for the second menu. Then I go right back to the display that the first picture shows. Also, I can't read anything on the screen.

---

### Post by heir4c on 2013-10-09
Have you windows on that laptop? if yes, can you boot up with windows? 

The menu here is like this:

resume       ____                resume startup
clean          ____                for freeing space
dpkg          ____                 repair brocken packages
failsafeX      ____               safe graphics modus
fsck          ____                  filesystem control
grub          ____                  for update grub
network    ____                   activate network
root         ____                    console for root
system-summary   ____      summary of system

You can use the console for root. I don't know directly a command but look for it on the forum, to remove or stop the driver from working. 

What you can do is add arguments like "nomodeset" via Grub: on the first line you click 'e' and than you can edit the "linux /boot" line. 
Also plug a extra monitor in the Laptop for control the screen of your laptop.

---

