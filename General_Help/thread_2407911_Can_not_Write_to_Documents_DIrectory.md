---
title: "Can not Write to Documents DIrectory"
date: 2018-12-11
forum: General Help
---

### Post by Jonners59 on 2018-12-11
I have just had to rebuild my PC.  It is dual boot with Windows 10 (yuk) with a common shared Documents folder/directory.

I have a mount point "Documents" and an fstab (/etc/fstb) entry
[HTML]#Entry for /dev/sda3 :
UUID=2104697C2776893B	/home/baroni/Desktop/Documents	ntfs-3g	defaults,rw,locale=en_GB.UTF-8	0	0[/HTML]

It worked fine, but recently I have been working a lot in Windows as there are 3D image slicing tools I need to use and now I fine that the Documents folder/directory is owned by root and not writable.  This is becoming a pain as documents build up on my desktop.

Any ideas how to fix this, please?

Could it be Windows is locking it?  I recall there was such a facility in Windows to aid fast booting....

---

### Post by Jonners59 on 2018-12-11
OK, assumption was correct:
Boot in to Windows
Type "Control Panel" in the search bar
Open the application and a list of sub applications appear.  Might need to show more by changing the view to small icons
Look for "Power Options" - an opportunity to make some tweaks
In one oif the settings to the left there are grey'd out options such as "Turn off Fast STartup".  Tick the show unavailable options and they un-grey.
Un-tick the "turn on fast startup"....
Save

reboot and although the folder is still owned by "root" it is read writable.....

---

