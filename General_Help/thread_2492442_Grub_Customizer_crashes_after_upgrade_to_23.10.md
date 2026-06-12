---
title: "Grub Customizer crashes after upgrade to 23.10"
date: 2023-11-11
forum: General Help
---

### Post by rooman62 on 2023-11-11
Grub Customizer crashes aftre upgrade to 23.10 	
 	 	[INDENT] 		When using 23.04 I installed and happily used Grub Customizer to  simplify dual boot menu for my wife who needs W10 for a work web site,  Ubuntu 23.10 is on a separate ssd and the boot default.

The error message shown on Grub Customizer startup;

 	Code:
 	Sourcing file 'etc/default/grub'
.
.
.many many menu entries here...
.
.

Adding boot menu entry for UEFI Firmware Settings ...
/etc/grub.d/proxifiedScripts/linux: version_find_latest: not found 


Then when I click the environment parameter button a pop-up shows a list of parameters, the following line indicates an error;

 	Code:
 	entry DEVICEMAP_FILE boot/grub/device-map 
when I do a search, this file and the aforementioned file in *proxifiedScripts* are missing in the system.

I have deleted and reinstalled Grub Customizer but no change.
Suggestions please. 	
[/INDENT]

---

### Post by tea for one on 2023-11-11
Proxified scripts again..........?
First, have a look at this info [https://easylinuxtipsproject.blogspot.com/p/grub-customizer.html](https://easylinuxtipsproject.blogspot.com/p/grub-customizer.html)

Do you have backups of both your Ubuntu and Windows 10 data?
Can you still boot into Windows 10 via PC boot menu?

---

### Post by Rubi1200 on 2023-11-11
As tea for one pointed out, make sure you have good backups for important data on Ubuntu and Windows. Also check if you can boot Windows.

Refer to section 7 of this thread:
[https://ubuntuforums.org/showthread.php?t=1664134](https://ubuntuforums.org/showthread.php?t=1664134)

WARNING: you need to be 100% sure you know what the default GRUB files are and where they are, what was modified by Grub Customizer, and how to try and undo the changes based on the link above.

The author of that thread, drs305, also has a comprehensive guide to GRUB2 and can be found here on the forum. 

If you are not sure, please don't make any changes.

A final note, we have seen so many problems here on the forum from users who installed Grub Customizer. 

In most cases, user changes can be easily implemented in the default GRUB files. These changes are consistent across version upgrades and rarely cause issues.

---

### Post by rooman62 on 2023-11-11
Thanks in advance for following, the urgence level is being scaled down as my wife will not be needing to access the computer for at least 3 days and any way I have prepared instructions for navigating in the menu to boot Win10.
I
Important data is backed up on external drives, yes.
I can boot into the default Ubuntu and equally Win10, yes.

I'll look at your suggestions to try and clean up and simplify this menu, thanks for the moment.

---

### Post by MAFoElffen on 2023-11-12
I have never recommended that anyone use Grub Customizer. I have recommended that people uninstall it and reinstall Grub2. It causes a lot of problems.

I do things for boot-repair and boot-info... And support users who have problems with their boot-loaders. Though not if they have Grub Customizer installed. Sorry.

Your error... /boot/grub/device-map was once upon a time a file that Grub used, if it existed, which meant you had to manually create it... But was found: NOT TO BE STABLE.

Here is Grub2's explanation on that: [https://www.gnu.org/software/grub/manual/grub/html_node/Device-map.html](https://www.gnu.org/software/grub/manual/grub/html_node/Device-map.html)

I will not comment anything else further on this. Sorry.

---

### Post by rooman62 on 2023-11-16
Grub customizer deleted, I'm going to reinstall Grub 2, thanks

---

