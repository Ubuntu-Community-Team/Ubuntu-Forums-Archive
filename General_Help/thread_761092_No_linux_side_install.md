---
title: "No linux side install?"
date: 2008-04-20
forum: General Help
---

### Post by Kanoga on 2008-04-20
Ok, so, I've installed Ubunutu with Wubi before, and everything worked fine, other than me having to download certain drivers for my video card.

That was quite a while ago, and I uninstalled Ubuntu, for whatever reason. Today I decided to try and install again.

First, I tried installing the 64bit version of Ubuntu with Wubi (The 64bit version is the one the installer chose to download)

I rebooted, Ubuntu starts up, and my monitor keeps switching between the Ubuntu screen when it's peach colored, before the login screen comes up, and an error screen for my monitor (VIDEO INPUT, D-SUB out of range), until eventually I'm at the login screen.

I put in the username and password I picked during installation, making SURE I am typing both correctly, and in the correct case, but it keeps saying invalid username or password. So I wait and let it log me in as "ubuntu"...and then my monitor goes back to it's error screen, then BACK to the login screen, so I reboot into windows.

I uninstall and reinstall numerous times, trying different installer modes (all of them) but I get the same problem, or the installer doesn't go through.

I then try the 32bit version, and I am getting the SAME problem.

Then it hits me.

I remember from before when I installed Ubuntu with Wubi a while back, there was an installation AFTER the windows installation which I assume set everything up (user accounts etc. etc.), then I reboot, and I'm ready to go.
Except this time...Nothing, it just tries booting Ubuntu without the 2nd installation.

:'(

Sorry if my post isn't any help, if you want me to be more specific just ask.

And I still have my logfile here, but it shows everytime I installed and uninstalled so I think theres too much to read for it to be of any use.

---

### Post by ago on 2008-04-21
Press esc at boot after choosing ubuntu and go for safe video mode

---

### Post by Kanoga on 2008-04-21
> **ago said:**
> Press esc at boot after choosing ubuntu and go for safe video mode

I tried that too, at some point when it tries loading I get a FATAL error and it just sits there unless I reboot my PC. I've tried all the other modes too.

---

### Post by ago on 2008-04-22
Can you try with the Live CD? That might well be a general issue, if you cannot boot off the live CD it might be that. Do you have a TV card (DVB-T or similar) by any chance?

---

### Post by Kanoga on 2008-04-22
Ok, after being frustrated with trying to install, I gave up after a bit.

Anyways, I decided it was time to do some cleaning up and started deleting useless things off my HD, and then i defragnented the drive. I had some extra space, so I decided to try and install with Wubi again, setting the disk space to 15GB instead.

It worked, and the installer runs and everything is fine, then I log in, it goes to the peach colored screen, then the screen goes black (I can still see my mouse cursor) then the cursor freezes, and it kicks me back to the login screen, I also tried booting into safe mode and the same thing happens.

I know another user also seems to have the same problem...

---

### Post by ago on 2008-04-22
The driver for your video card has to be installed.

[https://wiki.ubuntu.com/WubiGuide#head-e3a360bb3c91f569b4ab6f2d5a25521420e55bf3](https://wiki.ubuntu.com/WubiGuide#head-e3a360bb3c91f569b4ab6f2d5a25521420e55bf3)

---

### Post by Kanoga on 2008-04-23
> **ago said:**
> The driver for your video card has to be installed.

[https://wiki.ubuntu.com/WubiGuide#head-e3a360bb3c91f569b4ab6f2d5a25521420e55bf3](https://wiki.ubuntu.com/WubiGuide#head-e3a360bb3c91f569b4ab6f2d5a25521420e55bf3)

I tried using sudo dpkg-reconfigure xserver-xorg and there's no option to select a driver or anything.

---

### Post by ago on 2008-04-23
choose vesa to begin with, it's not the best one, but it works in most situation. Then see the restricted modules applet.

---

### Post by Kanoga on 2008-04-23
> **ago said:**
> choose vesa to begin with, it's not the best one, but it works in most situation. Then see the restricted modules applet.

How would I go about doing that?

---

