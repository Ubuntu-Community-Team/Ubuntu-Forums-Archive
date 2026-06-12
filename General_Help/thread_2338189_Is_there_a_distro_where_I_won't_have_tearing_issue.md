---
title: "Is there a distro where I won't have tearing issues with Nvidia?"
date: 2016-09-25
forum: General Help
---

### Post by gamelord122 on 2016-09-25
It sounds like tearing is a problem for a lot of Ubuntu users with Nvidia drivers, but I really just want a hassle-free, 'out-of-the-box' experience where I won't run into tearing issues.  The latest updates I got for my Nvidia drivers still haven't resolved my issues, which you can see an example of [here]("https://ubuntuforums.org/showthread.php?t=2332636&p=13526190#post13526190"), and [this link]("https://ubuntuforums.org/showthread.php?t=2298497&highlight=tearing") also details exactly the same issues I'm seeing.  It's a Lenovo circa late 2012, running an Nvidia GTX 660M and the 367.44 drivers.  Switching to older Nvidia drivers didn't seem to help at all, and switching to the Noveau or Intel drivers isn't really an option for me, because I'll never get decent gaming performance on those.  I just brought my laptop over to my girlfriend's apartment to show her RimWorld, but she almost got sick from me panning the camera around due to all of the tearing.  Something's gotta change here.

This also shouldn't be an unfixable problem, because my Alienware Steam Machine doesn't see any of these issues.  I don't want to put SteamOS on my laptop, but the problem with Nvidia drivers and tearing seems to be somewhat dependent on desktop environment.  [This page]("http://www.howtoeverything.net/linux/issues/finally-no-more-tearing-anywhere-mate-desktop-and-compiz") seems to have the last word on fixing these tearing issues, but only in MATE or while using the Noveau/Intel drivers.

Will I be able to avoid these issues entirely by switching to Ubuntu GNOME or Linux Mint?  Is there any distro I could switch to where this is a non-issue?

---

### Post by CantankRus on 2016-09-25
The solutions you point to instruct you to install and use compiz as the window manager in Mate.
Compiz is the default window manager in Ubuntu/Unity so don't see the need to install another desktop environment.
You can tweak the same settings by installing and using compizconfig-settings-manager (ccsm).

You could also install **gnome-session-flashback** as described in the second part of [**_[COLOR="#B22222"]this post[/COLOR]_**]("https://ubuntuforums.org/showthread.php?t=2272212&p=13258759#post13258759") and try playing with compiz in this DE 
or log into the session which uses Metacity as the window manager.

---

### Post by Keith_Helms on 2016-09-26
I don't think it's the Nvidia driver that's the problem, it's  specifically the Optimus hardware where you have dual Intel and Nvidia  graphics on a laptop for low-power vs. performance modes.  My desktop  system which has only an Nvidia graphics card works fine with no  tearing.  On my optimus laptop, I don't even bother trying to use the  Nvidia half and just watch video using the Intel graphics.

I  looked into it when I first got the laptop.  The problem was the Intel  graphics "owned" the display and the Nvidia graphics were unable to sync  to the vblank interval (my terminology may be off), meaning the driver  couldn't detect exactly when the screen was about to start being  repainted.  The driver developers were supposedly trying to come up with  a work-around, but I haven't seen any announcement of it being  released.

---

### Post by mc4man on 2016-09-26
Your mate link has nothing to do with optimus hardware. The issue of tearing is with nvidia-prime & xserver/mesa & no distro that uses Xserver atm has an official  fix for nvidia-prime. There are kernel/xorg patches to address this but they won't  be seen until the next xorg release so figure next year to show up in Ubuntu. (16.04.3 lts (hwe) *may* get the patched libraries &  kernel, that is about a year away..

If you were to install the 14.04.2/.3 image then it is [quite easy]("https://launchpad.net/~mc3man/+archive/ubuntu/tearfree-test") to use nvidia drivers thru nvidia-prime &  eliminate tearing. As far as 16.04 its possible but due to mesa/xserver changes not really without issues

---

