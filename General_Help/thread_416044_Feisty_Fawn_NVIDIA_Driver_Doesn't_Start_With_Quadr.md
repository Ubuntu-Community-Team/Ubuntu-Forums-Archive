---
title: "Feisty Fawn NVIDIA Driver Doesn't Start With Quadro FX 3450/4000 SDI"
date: 2007-04-20
forum: General Help
---

### Post by cousinzoidfarb on 2007-04-20
Hi,

I just installed Feisty Fawn on a system with an NVIDIA Quadro FX 3450/4000 SDI, according to the PCI ID.

I didn't receive any message about the use of a restricted driver when I started up. I went to System > Desktop Effects and was told that I need to enable the drivers. I hit enable and was told: Please run "desktop effects" again after restarting the computer, when the new graphics driver is active. I interpreted this to mean that they had been installed and I merely needed to restart. No such luck. I restarted, got the same desktop, and get same message when I go to System > Desktop Effects.

When I go to System > Administration > Restricted Driver Manager, the NVIDIA drivers are listed, but when I check the enable box and click the Enable Driver button, the checkbox is still clear, the circle is still red, and it still says "Not in use".

This card is listed as supported (PCI ID 0x00CD, [http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html](http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html)).

Anyone know how to fix this problem?

Thanks!

---

### Post by Theimon on 2007-04-21
You properly installed the nvidia driver and adjusted your xorg.conf accordingly? Otherwise it won't work.

---

### Post by cousinzoidfarb on 2007-04-21
If your assertion were true, I would expect the Restricted Driver Manager to say "Please install the 'X' package to enable this driver." or "Please refer to the 'Y' guide to properly configure your desktop environment for this driver." Instead, it doesn't seem to give any indication that anything changed or failed to change.

I read a while back that Feisty included the NVIDIA driver and enabled it out of the box (which was cause for some controversy). This doesn't appear to be true for my system, but isn't it supposed to be?

---

### Post by buchan on 2007-04-21
Ok so I was having this same problem and I got it figured out, just thought I'd let you guys know how ... 

The hint for me was ["this"]("http://http://lunapark6.com/ubuntu-704-feisty-fawn.html") page... its just a review of Ubuntu but it too mentioned the "happy clicky" method for getting the drivers.

Sure enough if you look half way down the page he even posts screen shots, in the screen shots he shows the file downloading after clicking the YES button... this was my "light bulb" as I was not seeing the download window after I clicked yes.

I had not done any updates to my new install so I ran the software updater and and changed the "Download from" under the preferences to a closer server, ran the updates and installed them.  After that I ran the "restricted software" link and told it to use the driver, this time when I clicked YES it downloaded the driver ... 

All looks good for me ... give this a try, I'm sure there are lots of other ways to do this but thats how I got mine to work... hope this helps anyone having the same problem.

---

### Post by cousinzoidfarb on 2007-04-22
Yes, it appeared to be an issue with the update manager. The driver is installed now.

I went to System > Administration > Update Manager (and gave my password), hit the Check button, and it installed a couple updates to the update manager. I also went to System > Administration > Synaptic Package Manager and made sure that Proprietary drivers for devices (restricted) was checked, under the Settings > Repositories menu. After this, the drivers installed fine.

Now just to get wide screen dual-monitors working!

Thanks for the help.

---

