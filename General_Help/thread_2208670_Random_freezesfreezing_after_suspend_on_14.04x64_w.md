---
title: "Random freezes/freezing after suspend on 14.04x64 w/Haswell+Prime GTX760M+xorg 331.49"
date: 2014-03-01
forum: General Help
---

### Post by patrick33 on 2014-03-01
Google-fu took me far, but my luck finally ran out.

I can't reliably use my PC when the Nvidia card is selected under Prime. 
Upon waking from suspend the desktop crashes, freezing on a white background with faint, glitchy blue/green designs. I can still access TTY with ctr+alt+F[], but that's of little use to me because my command line knowledge is limited.
The crashing also happens at random intervals. Rebooting seems to be my only solution.

I haven't done much beyond changing drivers, settings, and doing fresh installs. In terms of drivers the best results have come from xorg-edgers' 331.49 release. Before updating to that, even the integrated graphics would mess up. Occasionally when Intel graphics are on the touchpad will malfunction after suspend and only work if I hold down left click.

I'm determined to find some kind of fix for this, so any help would be greatly appreciated. Playing Steam games on Linux would be pretty cool.

Thanks!

Here's my laptop-- [http://us.acer.com/ac/en/US/content/model-datasheet/NX.M8SAA.004](http://us.acer.com/ac/en/US/content/model-datasheet/NX.M8SAA.004)
Xubuntu 14.04x64
Intel Haswell Core i7 4702MQ
12GB DDR3
Boot/install drive-- Toshiba SSD
Additional storage HDD
Nvidia Optimus GTX 760M w/xorg-edgers 331.49

---

### Post by Toz on 2014-03-02
*14.04 is still in beta. Moving to the **Ubuntu+1** forum.*

---

### Post by waspbr on 2014-03-21
I reckon that we will have to wait for nvidia to fix that bug, but so far I have been able to get around the freezes by using CTRL+ALT+F1  then CTRL+ALT+F7, this seem to break the freeze.

---

### Post by polki@mac.com on 2014-03-21
When you're in a TTY, log in and then try:

sudo service lightdm restart

If I'm right it should take you to the log-in screen.

---

### Post by patrick33 on 2014-03-25
waspbr-- thank you for the recommendation! Sadly it didn't work for me.

[email]polki@mac.com[/email]-- thank you, as well! Yours did work...to a degree. Restarting lightdm took me to a desktop environment, but the resolution was 640x480 and the aforementioned problems persisted. Re-restarting lightdm caused a total system crash that required a reboot.

---

### Post by Jimmie_Houchin on 2014-03-31
In my case I trace the problem to Light Locker. When I turn Light Locker off in the Light Locker Settings. Then I have no problems with my laptop suspending every time I close the lid. Also when I wake up from after suspend, everything works. It seems that it is a bug somewhere in Light Locker. 

Now of course this means you can't lock the screen either. Maybe this helps other experiencing this problem.

Jimmie

---

### Post by Chris Donahoe on 2014-04-21
I just fresh-installed 14.04 on my System 76 with Nvidia and am having the exact same problem.

---

### Post by cariboo on 2014-04-21
Moved to General Help, seeing as Trusty has been released.

---

### Post by Chris Donahoe on 2014-04-22
I just switched from the x-org open-source driver to the Nvidia proprietary driver through the "additional drivers" tab in "software & Updates", and it works perfectly on wake now. Hope that helps.

---

### Post by nqf52942 on 2015-01-27
hi there,


my Dell Vostro works fine with Ubuntu 14.04 LTS 64bit. the only thing is, when activate
the other video driver (default is X.Org-X-Server - AMD/ATI-Grafikdriver) the notebook hangs up after hibernation or standby.


when me use fglrx or fglrx-updates driver (for better performance), the notebook reproducible hangs up after hibernation or standby.


now me use the default open source driver. me only will report the error,when its an iusse from the closed source driver, and the community cant nothing do, delete my post.


respectfully, vostro 3550 user.
(i5-2450M CPU, AMD Radeon 6600M and 6700M Series, 8GB RAM)

---

