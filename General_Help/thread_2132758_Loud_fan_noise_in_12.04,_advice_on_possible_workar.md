---
title: "Loud fan noise in 12.04, advice on possible workaround"
date: 2013-04-05
forum: General Help
---

### Post by james_mcl on 2013-04-05
(I'll be cross-posting this to the mate-desktop.org forums, btw.)

The fan noise on my laptop has always been unusually loud when running Ubuntu, even though there's rarely a particularly high load on the CPU. I've typically assumed that this was due to having something as powerful as a Core i5 (and an Nvidia graphics card) occupying something as small as a laptop chassis - however, a set of events today suggested otherwise.

The update of the MATE (GNOME 2 fork) desktop environment from 1.4 to 1.6 didn't migrate my desktop settings, and one particularly noticeable aspect of the desktop - a desktop which had suddenly lost my custom theme, switched font smoothing off and touchpad scrolling back on, etc... was that the fan noise was absent for the first time.

(The custom theme apparently now had some other theme as a prerequisite, which wasn't installed. I THINK the GUI I was seeing instead might have been some sort of basic GUI which the nicer-looking themes are overlaid on top of.)

Now, I didn't notice precisely when it reverted to its loud self again, but I'm pretty sure fan noise went back up either when

a.) I disabled touchpad scrolling, or
b.) I set a close approximation to my custom theme up.

This suggests that either continuous handling of any change from default touchpad settings, or continuous work involved in overlaying "theme" versions of buttons, title-sections of windows etc on top of some bare-bones basic version, may be increasing CPU/GPU/other temperature to undesirable levels and thus triggering the fan - probably the GPU due to the low CPU usage levels.

(I don't actually know how to check GPU usage.)

Among the things I've tried to address this issue in the past have been:

* Installing the proprietary Nvidia graphics drivers. (later uninstalled due to their increasing the system font sizes)

* Installing jupiter, and looking in vain for a setting somebody claimed to have used to switch off external graphics so that the Intel CPU's internal graphics would do all the work.

* Adding the "Hardware Sensors Monitor" applet to the panel - unfortunately it's not clear which of the two temperatures corresponds to the CPU, and what the other one is the temperature of. (They're currently 57 and 63 degrees respectively, with only Firefox running.)

My laptop is a Lenovo Ideapad Z560, specifically chosen for its good track record running Ubuntu.

Can anyone suggest anything?

---

### Post by dalpi on 2013-04-13
Have you tried fixing the kernel power issue ([http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html](http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html)) or applying some power saving tweaks ([https://wiki.ubuntu.com/Kernel/PowerManagement/PowerSavingTweaks](https://wiki.ubuntu.com/Kernel/PowerManagement/PowerSavingTweaks))

---

