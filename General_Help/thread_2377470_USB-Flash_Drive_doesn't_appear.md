---
title: "USB-Flash Drive doesn't appear"
date: 2017-11-13
forum: General Help
---

### Post by eiffelsturm on 2017-11-13
Hey Community!

I have an issue with my Ubuntu 16.04 LTS (Well, it's old, but the reason is a bit difficult :D). My USB-Flash Drive does not appear on my Desktop. The Flash Drive works and the Port works, because I installed this system from a usb flash drive one hour ago. I already read every thread ( I guess) and did every suggestion but it still doesn't work. Do you have any suggestions, perhaps solutions? 

Thanks in advantage!!

---

### Post by yancek on 2017-11-13
Explain what "doesn't work" means.  As you posted, you just used it to install Ubuntu (right) so it does work.  
Are you using Unity?  Do you not see the flash icon in the panel on the Unity Desktop (if your're using it)?
Did you try looking under /media/username (substitute your actual username here)?
Do you still have the Ubuntu iso on it you used to install?

---

### Post by The Cog on 2017-11-13
I get the impression that the drive used to do the install was not the one that is now causing problems.

eiffelsturm, please can you plug the problem drive in, wait 10 seconds and then run these two commands:
```
dmesg | tail -20
lsusb
lsblk
```
and post the results

---

### Post by ajgreeny on 2017-11-13
And if this is the USB you used to install the Ubuntu system, how did you create the install medium; what did you use, mkusb, the dd command, or some other application?

---

