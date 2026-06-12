---
title: "Can't get Hibernate/Suspend to work at all, ever"
date: 2008-03-19
forum: General Help
---

### Post by inzania on 2008-03-19
I've been trying to get hibernate and/or suspend to work on my Thinkpad T60 laptop for some time now.  It's getting really frustrating, as it's not practical for me to use my laptop without at least one of these options.  I'm running 7.04, and have tried several methods, including the following:

1) sudo hibernate
This just gives me a black screen with a mouse on it for a moment, and then returns me back to where I was

2) sudo uswsusp s2ram
This takes me to a typical black screen-with-command-prompt asking for a login... but the computer is completely unresponsive and I can't type anything in at all, forcing me to hard-reboot the computer

3) sudo uswsusp s2disk
When I do this, uswsusp claims that I do not have a swap drive, but I clearly do... I've tried several times and confirmed through many means that I do, in fact, have a swap drive.  I've also done a "sudo dpkg-reconfigure uswsusp" , and again the reconfigure screen warns me that I have no swap drive.  Very frustrating.

4) Looking at the "power management" window...
I don't see any hibernate/suspend options anywhere... for example, closing the lid gives me only the "blank screen" option.

The laptop runs a ATI X1400 128MB card, I believe... I've heard there's trouble with graphics drivers with the NVIDIA chipset, but I thought uswsusp fixed that... I can't seem to figure out what else the problem might be.  I've tried upgrading to the 7.10 kernel, but couldn't get the OS to work at all (it seemed to just freeze my computer whenever I tried to boot, and I had to roll back).

Thanks for the help.

---

