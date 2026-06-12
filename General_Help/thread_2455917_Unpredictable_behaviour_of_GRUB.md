---
title: "Unpredictable behaviour of GRUB"
date: 2020-12-30
forum: General Help
---

### Post by RegUB on 2020-12-30
I have a Lenovo Thinkbook 15-IIL which came preloaded with Windows 10. I have installed Ubuntu 20.04, as a dual boot. 

Normally, if all is working well, when I power on I get a brief display of the manufacturer's splash screen, followed by the standard GRUB menu with the options Ubuntu/Advanced Options for Ubuntu/Windows Boot Manager/UEFI Firmware settings. There is a 10 second timeout after which Ubuntu is started by default, and boots OK.

However, intermittently, it doesn't always work like this, and there are two totally different scenarios which I will describe below as A and B.

SCENARIO A. GRUB menu appears as normal; however after selecting Ubuntu I get the messages 

"error: command failed
error: you need to load the kernel first
Press any key to continue"

Pressing a key takes me back to the GRUB menu, and the error repeats. However, I have found that if I now select "UEFI Firmware settings", then just exit without changing any of the settings, I get the GRUB menu again, but this time with a 30 second timeout, and Ubuntu now boots OK after a brief display of the messages shown in the photo below. (The 30 second timeout appears to be set in grub.cfg if the variable 'recordfail' = 1. But I don't really understand what is going on here).
[ATTACH=CONFIG]287651[/ATTACH]


SCENARIO B. This happens a lot less frequently. After switching on, the manufacturer's splash screen appears, but then the system hangs. No amount of key pressing (including the standard ESC & various F keys) will persuade it to go any further, and the only way to cure this is to switch the power off and on again, after which I usually get the GRUB menu and it boots OK.


So I can always boot the system eventually (so far!) But I would like to know what is causing the above problems and how to make GRUB work consistently.

---

### Post by oldfred on 2020-12-30
Have you updated UEFI from Lenovo? And SSD firmware?
And if you update UEFI, you may have to redo some settings as updates may change back to defaults.

Is Windows fast start up off?
That is often turned back on with Windows updates.
Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

If it works at least some of the time, not sure this will show much. But just to confirm details of install.
Lets see details, use ppa version with your live installer (2nd option) or any working install,  not Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by RegUB on 2021-06-30
Finally got round to doing something about this. Updating the UEFI (in Windows update!) solved the problem.

---

