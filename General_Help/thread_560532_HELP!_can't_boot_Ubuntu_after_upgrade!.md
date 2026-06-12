---
title: "HELP! can't boot Ubuntu after upgrade!"
date: 2007-09-26
forum: General Help
---

### Post by soumo on 2007-09-26
Hi all, 

I am a brand new user so bear with me.  I apologize for this verbose request.

I have Ubuntu installed via Wubi (ie. Ubuntu is installed into a virtual drive in a windows file NOT a partition) on a Lenovo 3000 N100 laptop with 1GB memory, 120GB hard drive, nvidia card, realtek audio etc.

I had Ubuntu running well, with the Beryl interface, but without sound or wireless.  I installed Ext2 Installable File system in Vista to gain access to my Ubuntu drives.  This failed as expected, however it did gain me access to my Lenovo service partition which was hogging 6Gbs.

I managed to get sound working via ALSA drivers.  I  had logged in back and forth between Vista & Ubuntu no probs.  I decided to delete most of the service partition's contents minus the boot folder (I have them backed up on dvd as well as obtained the recovery dvds from Lenovo in case) to see if the computer would run.  It did.

I decided to install the Akamaru/Kiba dock in Ubuntu (the one from the Vista vs. Ubuntu youtube video), and in the process realized that my gcc is not up to date, as well as a ton of dependencies.  

I got somewhat through the process of installing, but stopped short of the jpeg, tiff etc. libraries.  I planned to carry on later.  In the meantime I logged on to Vista, where I noticed something strange.  My sound scheme had changed to give the system sounds for things like maximizing windows, closing them, same for context menus -quite annoying!  Not sure why this happened.

Now when I tried to get into Ubuntu on boot I get:
"
...
<something about my 8139c or 8139cp driver being wrong and to try the 8139too driver instead (I think this is sound?)>
...
[B]Check root = bootarg cat/proc/cmdline or missing modules, devices: cat /proc/modules ls /dev ALERT! does not exist.  Dropping to a shell!
...
BusyBox...(...Deb...)  Built-in shell (ash)

/bin/sh: can't access tty; job control turned off
(initramfs)
[/B]"

If I try any of the menu options, I get this or I get a hang on the Ubuntu loader screen (the progress bar goes to a full box and about ¾ of the next box).

[http://ubuntuforums.org/showthread.php?p=2505697](http://ubuntuforums.org/showthread.php?p=2505697) 
seems to be related to my problem, but it's really beyond me.

I have done a google search but come up with entries that don't make much sense to me.

Can someone tell me what is wrong, or how to go about researching this?  Please explain in baby-steps if possible.  Part of the problem is that I have made so many changes to my computer that the exact order may have escaped me, and I do not want to do a fresh install of either system.  I have spent a long time tweaking Ubuntu and Vista so would like to really gain an idea of what the exact problem is and where to go.  

I have a Ubuntu live cd.

-Thanks in advance!

---

### Post by reckless2k2 on 2007-09-26
yeah this belongs in the wubi area. i'm sure you can find a million people over there with the same issue.

---

### Post by soumo on 2007-09-26
Thanks, I will post this over!

---

### Post by soumo on 2007-09-26
Update:
I have moved this here if anyone feels like contributing:

[http://ubuntuforums.org/showthread.php?p=3430827#post3430827](http://ubuntuforums.org/showthread.php?p=3430827#post3430827)

---

