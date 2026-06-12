---
title: "Xubuntu - set screen rez from recovery mode"
date: 2007-11-03
forum: General Help
---

### Post by Optiker on 2007-11-03
I've installed Xubnutu on an older Micron. It installed and ran fine. but being the tinker that I am, I had to try and toy with the settings. Unfortunately, through a series of "try and see what happens" changes, I am now at a point where the rez is set too high, so that when Xubuntu boots, the display is badly scrambled so that I can't get back in to reset to a lower rez. I've corrected this problem before with a live CD, but don't recall how, and not with an installed system.

I am currently sitting in the "restore" boot mode, but am not very experienced at CL operations. I dug around a little with HELP and MAN pages, but didn't know how to pause after a full screen, so ended up justs viewing the last screen full of information - so wasn't able to find anything useful. I don't know how to launch a program from CL - for example, a text editor - and don't know where the conf file that would be equivalent to the graphics config file in KDE is - so can't edit that conf file manually at this point.

Can somebody walk me through how to recover the original display setting, or at least get back to a setting where I can go in and edit it from the gui? I think I can do it from the recovery mode if I know what to enter in the CL. One of the referenced links suggested the auto config utility, but I don't know how to do that from the CL.

Your assistance is greatly appreciated!

Thanks!
Optiker

---

### Post by Optiker on 2007-11-03
Describing solution for the benefit of others who might have similar problem and searching for related posts.

Wasn't seeing an answer or finding anything while searching, so with nothing to lose, dug around until I was able to get into the right directory, fumbled through "man" and "info" commands till I figured out how to delete and rename files, deleted the current bad xorg.conf, and renamed the first backed up one (original default?) from xorg.conf.1 to xorg.conf. Kind of a sledgehammer approach, but seems to have gotten me back to my original settings.

Optiker

---

