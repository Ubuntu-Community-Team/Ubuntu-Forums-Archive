---
title: "Monitor goes to sleep and wont wake up"
date: 2019-09-14
forum: General Help
---

### Post by Kusho on 2019-09-14
Using Ubuntu 19.04.  This problem just started a day ago.  I dual boot and does not happen in Windows.  I have both Windows and Ubuntu set to put my monitor to sleep after 15 minutes.  I don't put my PC to sleep thou.  I use Setiathome and want that to continue to run.  Anyway, in Ubuntu now, since a day ago, whenever I come back to my pc and try to wake up the monitor it will not wake up.  The computer is still on, but nothing I do will wake it up.  The only thing I can do is power off my computer, and power it back on.  I'm thinking this was an update to ubuntu.  I did install Google Chrome yesterday but doubt that would cause this.  Any thoughts?

Video card is Nvidia GeForce 560.  Monitor is Acer KG1 series 27inch.  Don't know what else you might need to know.....

---

### Post by Kusho on 2019-09-14
Maybe it was just a sign of my monitor going out.  I turned Ubuntu to never put the monitor to sleep and turned off the monitor manually when I went to leave.  Well now the monitor won't turn back on.  I have tried unplugging it and plugging it back in.  I have even unplugged the HDMI cable but it still won't turn on.  Looks like this monitor is just dead.

---

### Post by Kusho on 2019-09-18
Ok this is not fixed.  I got a new monitor and I get the same problem.  When Ubuntu puts my monitor to sleep nothing I can do wakes it up.  It only happens in Ubuntu, not Windows.  I tried uninstalling Google Chrome as that was the only change I made when this problem started, but that did not fix it.  I am wondering if I just happened to get a new update of my graphics driver that day and that is causing it.  I will try to figure out how to roll that back to an older version.  Other than that I don't know what to try.  If I have to I will change the Grub boot order to boot by default into Windows instead of Ubuntu and just give up on Ubuntu for now.  This problem of not waking up is that bad.

---

### Post by Kusho on 2019-09-19
Just posting again to nudge the post and maybe someone will see it.  If there is a different way to get posts to show up again let me know.

---

### Post by uRock on 2019-09-19
> **Kusho said:**
> Ok this is not fixed.  I got a new monitor and I get the same problem.  When Ubuntu puts my monitor to sleep nothing I can do wakes it up.  It only happens in Ubuntu, not Windows.  I tried uninstalling Google Chrome as that was the only change I made when this problem started, but that did not fix it.  I am wondering if I just happened to get a new update of my graphics driver that day and that is causing it.  I will try to figure out how to roll that back to an older version.  Other than that I don't know what to try.  If I have to I will change the Grub boot order to boot by default into Windows instead of Ubuntu and just give up on Ubuntu for now.  This problem of not waking up is that bad.

I'm thinking it is likely a graphics driver issue. I have a machine that does that also, but only started doing that after I uninstalled the graphics driver. I went through and changed setting so the screen doesn't go to sleep. Ubuntu recently started installing graphics drivers for nvidia by default and it seems to be causing issues for a lot of people.

BTW, please wait at least 24 hours before bumping your threads.

---

### Post by Kusho on 2019-09-19
How do I change the settings for Ubuntu to not go to sleep?  I set it to not blank the screen but it still goes to sleep.  And I have a change on this.  I am having this issue now in Windows as well as Ubuntu.  Only difference is when I tell Windows to not put the screen to sleep it actually does. (Correction.  Windows still puts the monitor to sleep also.  Even thou it is clearly set to never put the monitor to sleep.)  So I have the same problems in both Windows and Ubuntu.  Thinking I need a new video card.  It was way old anyway...  so its probably time.

And on your BTW, I still don't know HOW to bump my thread.  Is that just make another post?  Noone has explained it.

---

### Post by Kusho on 2019-09-22
A friend came over and updated my Nvidia video drivers and now in Windows it will go to sleep and wake up or it will go to screen saver and not go to sleep.  But only if I do not run BOINC (Setiathome)  For some reason if I run BOINC after a few minutes of inactivity the screen will go to sleep and never wake up. It also doesn't seem to matter if I have windows set to put my monitor to sleep or not.  Either way if I'm running BOINC the monitor will go to sleep. I don't know how this is connected to the issue.  I tried booting into Ubuntu and not running BOINC but the monitor still goes to sleep after a few minutes of inactivity and will never wake up.

Still waiting on a new video card.  Ordered it from Newegg so it will get here this week.  See what that does for this issue.

---

### Post by Impavidus on 2019-09-23
Sometimes it helps if you go to one of the consoles, then back to the gui: ctrl+alt+F6, ctrl+alt+F7.

---

### Post by Kusho on 2019-09-28
Bought a new graphics card...  but looks like this card doesn't have ubuntu 19.04 drivers yet.  
Sapphire PULSE Radeon RX 580 8GB GDDR5 PCI-E Dual HDMI / DVI-D / Dual DP OC w/ Backplate (UEFI), 100411P8GOCL
Sold and Shipped by Newegg

This issue of Ubuntu going to sleep and never waking up is now solved, so it was somehow related to my old video card.  Now I just need a graphics driver for Ubuntu. Looking like I bought the wrong video card to use Linux.  Short of that I need to figure out how to default grub to boot into Windows.  I know this was not hard to do, but without finding a post that tells me how to do it I cant do it.  Anyway I will mark this problem as solved.

---

### Post by rbmorse on 2019-09-29
I see this behavior on my 2080RTX with the Nvidia 435 drivers.  Something in the way Nvidia is handling HDMI.  Problem does not occur when using a DP connection.

---

