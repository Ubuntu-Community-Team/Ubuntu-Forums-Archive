---
title: "keyboard problems in grub"
date: 2007-06-07
forum: General Help
---

### Post by bobmarksdale on 2007-06-07
I recently installed 6.10 from a disk that I've had lying around for a while.  I changed the grub file so that the default OS is windows as not to confuse my parents overly much.  But, whenever I boot and try to use the arrow keys to switch to Linux, the little message that says "the selected OS will boot in X seconds" goes away and all I can do is hit enter because the arrow keys will not move the selector thingy.  Is this a keyboard problem or a Linux problem?  My keyboard is a M$ IntelliType Pro (if that helps).  Also, I cannot currently access linux at all, so any way to change this would be nice.

---

### Post by mikewhatever on 2007-06-07
Do any other keys work? If that's a USB keyboard, the following post may help
[http://ubuntuforums.org/showthread.php?t=462100&highlight=usb+keyboard](http://ubuntuforums.org/showthread.php?t=462100&highlight=usb+keyboard)

---

### Post by bobmarksdale on 2007-06-07
The other keys work.  Actually I just tried rebooting and after about 30 seconds of mashing the keyboard in anger, I could go up and down.  Idk why, but now I'm in Ubuntu and I'll try the BIOS thing next time.  Thanx.:D

---

### Post by bobmarksdale on 2007-06-07
I actually figured this out by trial and error, but numlock was on and when I turned it off, the arrow keys worked fine. :D (I am only posting this in case someone else has the same problem.)  But, one more question:  When I updated from 6.10 to 7.04, in my boot menu there are now 6 different ubuntu options (3 normal and 3 safe mode) when I only really need one of each.  Any ideas on how to get rid of the other 4?  (not really a major problem, but I like to keep my computer tidy)

---

### Post by mikewhatever on 2007-06-08
Those are the older kernel versions you do not need. If everything works with your current kernel, uninstall the older ones from Synaptic. Just search for the appropriate numbers, which I guess are 2.6.17-10, 2.6.17-11 and 2.6.20-15.
To remove the entries from the grub menu, delete them from the menu.lst file
> gksudo gedit /boot/grub/menu.lst

---

