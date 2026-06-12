---
title: "drive checking?"
date: 2007-10-06
forum: General Help
---

### Post by panguin on 2007-10-06
So when i turned on the Lappetron 3000 this morning, after the GRUB loaded, it gave me the following message.

/dev/sda1 (i think) mounted 35 times without being checked, forced check.

then there was an ascii progress bar for a couple minutes, and then it loaded.

so, should i be concerned, or is this something that was in the manual that i didnt read?

also, is there some way to manually check the drive, so as to prevent the drive from being checked when i am in a time crunch?

thanks in advance!

---

### Post by tenmillionmilesaway on 2007-10-06
Don't worry about it, its normal.  As for stopping the check i don't know, sorry.

Richard

---

### Post by zach12 on 2007-10-06
I get that all the time :evil:

---

### Post by snickers295 on 2007-10-06
its nothing so don't worry.
its just giving the hard drive a check up.

---

### Post by spb37 on 2007-10-06
Anyone know a way to abort the drive check or initiate it manually for a partition.  Thx

---

### Post by ajgreeny on 2007-10-06
Ubuntu normally does this check every 30 boots, but that can be changed using tune2fs in a terminal.  Look at ```
man tune2fs
``` for details.  I have my system set to check every 80 boots by using the command ```
sudo tune2fs -c80 /dev/hda2
``` but you may need to change the **/dev/hda2** part to match your system.
To answer your final point, I think Ctrl+c will stop the check, but I'm not certain.

---

### Post by expatCM on 2007-10-06
Autofsck was released a month or so ago.  It is a great utility.  What it does is change the time that the fsck event takes place.  When you come to shut down your computer, if it is time for a fsck then you get a message which says time to do it, can it be done now. If you say ok then the system will restart itself, run the fsck and then shut down the system.  It no longer appears at power on.  

Easy.  No time wasted.

[https://wiki.ubuntu.com/AutoFsck](https://wiki.ubuntu.com/AutoFsck)

---

### Post by panguin on 2007-10-06
thanks everyone!

see? this is why i completely got rid of microsoft.

cause if anything like this happened in windows, i would have had to do a bug report probably, and then 3 months later recieve a very politely worded "bugger off" from the big hq.

*hugs ubuntu community*

I LOVE YOU GUYS!!!!!

---

