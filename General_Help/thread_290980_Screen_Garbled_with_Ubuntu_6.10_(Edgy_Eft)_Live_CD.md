---
title: "Screen Garbled with Ubuntu 6.10 (Edgy Eft) Live CD"
date: 2006-11-01
forum: General Help
---

### Post by BenK1976 on 2006-11-01
I currently have Ubuntu 6.06 LTS (Dapper Drake) installed on my Dell Inspiron 5000e laptop.  It has 256 MB of memory, an Intel Pentium III 850 MHz processor, and an ATI Technologies Inc Rage Mobility M3 AGP 2x (rev 02) video graphics adapter.

Ubuntu Dapper Drake runs very well on this laptop.  It is the best linux distribution I have used so far.  I have tried Slackware, Fedora Core, and Debian.

However, I would really like to upgrade to Edgy Eft.  I am not willing to do the upgrage until I can verify that it works on my laptop in the Live CD environment.  That is where I am having trouble.

When I boot into the Edgy Eft Live CD environment the screen is very garbled.  The Daper Drake Live CD environment had the same problem when I did not choose the safe graphics mode but worked flawlessly when I did select the safe graphics mode.  Unfortunately this does not work in the Edgy Eft Live CD environment.

I have seen a post titled "Guide for those with garbled video on Edgy LiveCD" that suggests that I "use the alternative install CD" and "use the text-based install" and then modify "/etc/X11/xorg.conf."  The post can be found at <http://ubuntuforums.org/showthread.php?t=287526>.  However, I would really rather not insall Edgy Eft until I know it will work correctly in the Live CD environment.

What I have tried so far.

I did a fair amount of research and found some information that suggested that display problems could be fixed by boot parameters.  I have tried the following boot parameters:

* vga=771
* vga=0x31b
* video=aty128fb
* video=aty128fb:1600x1200x32bpp@60
* video=vesafb

None of these seemed to help.

Can someone offer any aditional suggestions on how to get the Live CD environment to work correctly or am I going to take a leap of faith and follow the suggestions given in the post titled "Guide for those with garbled video on Edgy LiveCD?"

I look forward to any help you all might have to offer.

---

### Post by BenK1976 on 2006-11-03
As it turns out, I found the answer to my one question when I read one of the replies to the post titled "Guide for those with garbled video on Edgy LiveCD" ([http://ubuntuforums.org/showthread.php?t=287526](http://ubuntuforums.org/showthread.php?t=287526)) more carefully.  Ramiro replied as follows:
"""actually you don't need to download a completely different cd

when you get the garbled screen just hit ctrl-alt-f1 to get to a console. it should be logged in automatically

then type sudo nano /etc/X11/xorg.conf and follow the instructions of the above post. When you restart gdm, it should be working and you can install.

once that's done your installed version should also be using the vesa drivers, I recommend you upgrade to the nvidia drivers straight away"""

Given this information I solved my problem as follows:
(1) Boot from the Ubuntu Live CD and choose "Start or Install Ubuntu."
(2) When Ubuntu starts and displays the garbled screen, press Control + Alt + F1 to get to a console.
(3) Run "sudo nano /etc/X11/xorg.conf" and change
    Driver   "ati"
in the Screen section to
    Driver   "vesa"
Then save xorg.conf.
(4) Press Control + Alt + F7 to return to the garbled Gnome desktop.
(5) Press Control + Alt + Backspace to restart GDM.

From there on everything works perfectly!

---

