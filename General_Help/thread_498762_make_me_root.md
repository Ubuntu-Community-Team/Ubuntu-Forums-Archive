---
title: "make me root"
date: 2007-07-11
forum: General Help
---

### Post by longlegs on 2007-07-11
Hi !
1:  I know there are some reasons for not having me as root all the time, but this is MY computer, and I'm %^$# tired of being told Permission Denied, File is not yours, You dont, you cant... 
How do I change the OS "Ubuntu 6.10" so that this keyboard and mouse are root/chief/honcho/boss/the Man/do what you're told or die, at least for this session?

2:  I have installed Ubuntu 6.10 and it all works except USB internet connection. However, on reboot I can't get it to load except using a "Super Grub Rescue" cd.
Unfortunately the only thing I can get the cd to do is boot my ubuntu. I can't get the install fixed so the dual boot is normal
Can any one give me the correct sequence of commands to use in terminal to add grub to the right partition, and how to modify  boot.ini to call grub to boot Ubuntu?
I have a SCSI with 5 partitions, a small IDE with 2 partitions and a large IDE with 3 primary partitions (hda1, hda2, hda3 ) 1 extended partition (hda4) containing 4 logical partitions (hda5, hda6, hda7, and hda8 ). hda1 thru hda5 are used for other OS's. Ubuntu is loaded on hda8, swap on hda7, and hopefully hda6 (a 120Mb partition) will be the /boot containing grub and the boot menu.lst stuff.
I notice that it (in file browser) has a grub folder, but hda8 has a /boot folder containing grub folder also.
Any help?

TIA
longlegs

---

### Post by travist120 on 2007-07-11
The first question, I know how to answer. Still not a good idea though

Go to system
--->Administration
------>Login Window.

From there click on security. then check off "Allow local administrator login." 

Be sure to change your root password from default too. Then logout, and at login screen type in root, and then pass. Very very very dangerous, and I recommend that you just use "sudo chown" command instead. cause it just changes the ownership to you, and you can change it back.

---

### Post by longlegs on 2007-07-11
Thanks, that will save me a lot of  frustration.
longlegs

---

