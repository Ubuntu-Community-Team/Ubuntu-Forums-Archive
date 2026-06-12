---
title: "Assistance in installing 16.04 on new SSD drive"
date: 2016-12-09
forum: General Help
---

### Post by lsutiger on 2016-12-09
I am having problem after problem trying to get this to work. I had a working 16.04 gnome flashback session on my HDD. I still have the drive and it still boots. I bought a new SSD drive and I am attempting to get a good installation on it.
Here what has happened within the last 24 hours:
Clonezilla - Failure. After reading some I understood a new install should be successful as a cloned drive from HDD to SSD does not work.
16.04 Unity Install from USB - fails during install- States that it can not copy complete copying files. Thought it may be a bad flash drive. Changed drives.
2nd install from new USB drive - Same as above.
16.04 Unity Install from DVD drive - same as above. 
Download new image. Same as above.
16.04 Gnome USB install (from second USB drive) - Success! Tried to install gnome-session-flashback. States install is completed. Log off to log into Gnome Flashback - is not listed. There is Wayland and Gnome Classic. Booted to both of those, brings me to the Gnome desktop.
16.04 Network install - Successfully installs but does not boot. Grub CLI. Attempted rescue, grub fails to install.
UEFI is enabled. There is an item in BIOS labelled ubuntu. This was there from the previous two installs (14.04 and 16.04).

If someone can point me to how to get gnome-session-flashback to work with the Gnome install that would be great. I really do not like the ascetics and how the Gnome desktop flows.

---

### Post by karl96 on 2016-12-09
Hi, i'll answer the gnome classic question first.

You can download extentions using the gnome-tweak-tool (may need to install). You can add a bottom panel, places list, applications list, etc, etc, make it look exactly the same.

---

### Post by oldfred on 2016-12-09
I am running flashback or gnome panel in Ubuntu. It works for me.
[https://ubuntuforums.org/showthread.php?t=2302432](https://ubuntuforums.org/showthread.php?t=2302432)

I prefer new clean installs over copy to a new drive. You can copy /home, perhaps some settings from /etc and export list of installed apps in old install and use that to reinstall in new install.
       Oldfred's list of stuff to backup May 2011 (still mostly current, see added links below):
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
Adding extra commands to rsync 
[http://ubuntuforums.org/showthread.php?t=2260658](http://ubuntuforums.org/showthread.php?t=2260658)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
[http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders](http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders)

Is system UEFI or BIOS. Are your installs UEFI or BIOS?
       
 May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by leunam12 on 2016-12-10
Have you tried Ubuntu Mate?

---

### Post by lsutiger on 2016-12-10
I decided to go with Mate. Not exactly the same as before but dang close. Need to find a way to change the window decorations. Can't find an install candidate for Emerald, which I had installed on the HDD(16.04). Do not remember how I got it installed as it was months ago.
@oldfred for some reason I can not get Unity to install without crashing. Flashback is what I had installed on my HDD. Thanks for all of the links and info! It is UEFI.

---

### Post by lsutiger on 2016-12-10
I decided to go with Mate. Not exactly the same as before but dang close. Need to find a way to change the window decorations. Can't find an install candidate for Emerald, which I had installed on the HDD(16.04). Do not remember how I got it installed as it was months ago.
@oldfred for some reason I can not get Unity to install without crashing. Flashback is what I had installed on my HDD. Thanks for all of the links and info! It is UEFI.

---

### Post by leunam12 on 2016-12-21
To change the windows decorations just right-click on the desktop and select "change desktop background" and then click on the theme tab, it will let you customize your theme and select your window decorations.

---

