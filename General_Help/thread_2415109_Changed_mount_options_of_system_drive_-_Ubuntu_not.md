---
title: "Changed mount options of system drive - Ubuntu not starting anymore"
date: 2019-03-20
forum: General Help
---

### Post by speedymcs on 2019-03-20
I just did something stupid. Using gnome-disks Ubuntu 18.04 I changed the mount options of my drive /sda1 where Ubuntu is installed. I had been tinkering with the mount options of a second hard drive, trying to mount it automatically on startup, but that last time I absent minded changed an option of the drive with the OS. Yes there was a distinct warning message, and no I don't remember the setting I changed - I think it was the mount name. The machine then booted to a black screen, then to emergency mode, then to a black screen with a blinking cursor line. Can I salvage this?

---

### Post by The Cog on 2019-03-20
Yes. But I think you will need to boot an installer live CD to use as a rescue CD. With that you can open the sda1 root partition (it may not be sda1 if you foot from the installer, use the command **lsblk** to check). Then you can edit etc/fstab and make the required changes The mount point should of course just be / .If in doubt you can post the contents of fstab here and people will be able to help.

---

### Post by speedymcs on 2019-03-20
Thank you so much for the quick reply! I had luckily made a backup of the old fstab and was able to revert it without a problem using an installer CD. I also managed to set the correct settings for the other drive that I actually wanted to change, this time editing fstab directly. Using the GUI sometimes feels like a shortcut I guess but isn't really, after giving it a minute the humble text file seemed much more intuitive. Thanks for the help :)

---

