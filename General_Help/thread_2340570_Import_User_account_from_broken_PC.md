---
title: "Import User account from broken PC"
date: 2016-10-19
forum: General Help
---

### Post by simon114 on 2016-10-19
Hi community,

1)My laptop Died, 
2)I bought a new one.
 3)Hard Drive from broken pc in an external case sata to usb 3.0.

Question -  How can I create a user account backup (if possible) from the hard drive from broken computer
Question - If question 1 is possible, How can I import that backed up account into my new laptop.


Thanks for any help...Love Ubuntu 16.04 Best ever!!!!:KS

---

### Post by Portaro on 2016-10-19
If you have conection to the hard drive (disk) you only need to mount this an simply move to the /home/user path and choose the files that you want to copy a simple move it to your new disk and pc . 
You also can use the old disk with your new pc and probably continue to use the /home/user path also Ubuntu System but its probably that you need to reinstall the system on / because the hardware change or try a update upgrade in text mode and see if the system works well and reconfigure services like sensors etc to the new hardware.

I think that its all I can suggest, to copy files you can use a GUI mode or terminal with command **cp** and to move use **mv** command.

---

### Post by simon114 on 2016-10-29
yep, thankyou, that solved it, I was also able to copy the .mozilla folder and put it into the new install, restoring everything, passwords, speed dial the whole lot. Thanks a million.

---

