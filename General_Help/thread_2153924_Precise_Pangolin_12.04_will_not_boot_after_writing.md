---
title: "Precise Pangolin 12.04 will not boot after writing dvd to .iso"
date: 2013-06-12
forum: General Help
---

### Post by Mark_in_Hollywood on 2013-06-12
Using the dd command to write two .iso-s to the /media folder, upon trying to use gksugo thunar (or even nautilus) to move the .iso-s to my desktop (home/Mark/Desktop) I could not. I re-booted (twice) but neither time would the OS come up. It hung both times. I re-booted out with Alt-SysRq R E I S U B K. Now I'm in Live-USB mode and need help getting the OS up and running. The OS usually shows the 12.04 splash screen, but now it's showing code of some sort, ending with a line about Timidity.

---

### Post by searchfgold6789 on 2013-06-12
The dd command isn't what you want to use for writing dvds (as you now see). It is a file copier, in a sense, but it doesn't copy files themselves, it copies raw data. So you have probably messed up your filesystem. I wonder what is the exact command you used.
This is an interesting problem and data corruption is a tricky issue, you could try just making a new folder named "media" in Live USB mode, and then use the dd command to write this folder raw to its original location on the hard disk.
But the only surefire way of fixing this now is to backup your data and reinstall.

---

### Post by Mark_in_Hollywood on 2013-06-12
Here is the terminal command

dd if=/dev/cdrom of=image_name.iso

so I did:

sudo dd if=/dev/cdrom of=image_<source_code>.iso (Source Code is a theatrical movie). The first time I ran this, I forgot ".iso" at the end. So, dd balked and returned something now lost to my memory. I ran dd again and added the .iso filename extension. Again, dd balked returned some strange info.

BUT, earlier today, before the dvd copying, while trying something or other that needed sudo, the OS 3 times returned incorrect password. The 3rd try cannot have been wrong and my keyboard does type those characters correctly.

For what it's worth, I got the idea for using dd from here:

[http://askubuntu.com/questions/147800/ripping-dvd-to-iso-accurately](http://askubuntu.com/questions/147800/ripping-dvd-to-iso-accurately)

---

