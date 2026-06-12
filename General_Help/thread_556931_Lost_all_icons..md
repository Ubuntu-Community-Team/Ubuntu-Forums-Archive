---
title: "Lost all icons."
date: 2007-09-21
forum: General Help
---

### Post by Tolgak on 2007-09-21
In trying to unlock the computer for a moment to install a mouse pointer theme, I lost the entire folder. Everything. It's my own fault too.

The Psychocats have a tutorial page that has a line "sudo rm -r /usr/share/icons/themename"  before mentioning how to unlock security with the "gksudo nautilus" command.

It took me an hour to find a page that offered the latter line, but I was so frustrated that I entered the first line (without the 'themename') without thinking about it.

Now, my entire /usr/share/icons folder has been deleted. Without it I cannot get online, because the network manager's icon file is missing.

I tried running the CD and extracting the files from there, but it refuses permission to copy the files outside of the system.

So what I need is for somebody to send me or link me to the download of the original 'icons' folder (as if you just installed ubuntu), because I cannot do it myself.

If you can tell me how to extract the 'icons' folder from the cd, I would also appreciate that. No sudo function is working when I try that method.

Thank you.

---

### Post by dcstar on 2007-09-22
> **Tolgak said:**
> In trying to unlock the computer for a moment to install a mouse pointer theme, I lost the entire folder. Everything. It's my own fault too.

The Psychocats have a tutorial page that has a line "sudo rm -r /usr/share/icons/themename" before mentioning how to unlock security with the "gksudo nautilus" command.

It took me an hour to find a page that offered the latter line, but I was so frustrated that I entered the first without thinking about it.

Needless to say, I need my icons back. Anybody know how they can be recovered? Not even the logout button has the correct icon.

Try selecting another theme from System-Preferences-Theme, and then changing back to the original one.

---

### Post by Tolgak on 2007-09-22
Information about my situation has been updated.

Sorry dcstar, your method didn't work.

---

### Post by Tolgak on 2007-09-22
Bump

---

### Post by aysiu on 2007-09-23
Boot off the live CD. Mount your regular Ubuntu installation. Then copy the icons from the CD to your hard drive.

To mount your Ubuntu installation, you'd do something like this: ```
sudo fdisk -l
``` Figure out from the output what drive your installation is. Let's say, for example, that it's */dev/hda1*. Then, create a mount point for it: ```
sudo mkdir /recovery
``` and mount it there: ```
sudo mount -t ext3 */dev/hda1* /recovery
``` Finally, copy the CD's icons to your hard drive's icon folder: ```
sudo cp -R /usr/share/icons/* /recovery/usr/share/icons/
``` **Note**: Ubuntu is not necessarily /dev/hda1. I put *dev/hda1* in italics, because that could be something else, depending on the output of *sudo fdisk -l*.

---

