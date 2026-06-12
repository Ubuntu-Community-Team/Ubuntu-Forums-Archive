---
title: "Ubuntu destroyed my usb"
date: 2015-12-13
forum: General Help
---

### Post by Aaronyoman on 2015-12-13
Hello everyone earlier today I tried formatting my usb and wiping it entirely. I made it replace everything with full zeros. With no dialogue menu or any GUI screens I decided to take it out thinking maybe it is done. I tried inserting it into my netbook multiple times even after restarting it. Along with a mac and my xbox none could read it. I am running ubuntu 15.10 on cheap Acer aspire one 522 netbook. Please help me

---

### Post by grahammechanical on 2015-12-13
Your thread title is incorrect. You are responsible for the tasks that you set the utility you were using. Have you tried formatting the USB drive? And then seeing if a Linux OS will read it? Utilities that format drives are often better at detecting than file managers.

---

### Post by Bucky Ball on 2015-12-13
Welcome. Install and open Gparted. Plug the drive in and launch Gparted. Use the drop-down list at top right to get to the USB. From the 'Device' drop-down (I think but you'll find it) choose 'New partition table'. Write the partition table. Right click the free space and 'New'. Can you create a partition.

And yes. Ubuntu had nothing to do with this. You have given us no idea of how you wrote zeros on the USB or what software you used to do it (program, not operating system). You also pulled the stick without knowing whether it was 'cooked'. :)

Hopefully this is fixable.

---

### Post by sudodus on 2015-12-14
See also this link: [Pendrive lifetime]("http://ubuntuforums.org/showthread.php?t=2196858&p=13199297#post13199297")

---

### Post by yancek on 2015-12-14
> I made it replace everything with full zeros. With no dialogue menu or  any GUI screens I decided to take it out thinking maybe it is done. 

Overwriting is not formatting.  If you tried to overwrite with all zeros from a terminal, you would have known it was finished when it returned to the original prompt.
Is it recognized in the BIOS?
If you did not format it, there is nothing to recognize so follow the instructions suggested above to create a partition table and format.

---

### Post by buzzingrobot on 2015-12-14
Don't be in a hurry.  I just zeroed out an 8-gig USB stick: 50 minutes. Zero'ing out an external drive of any common size is going to take hours.

---

### Post by efflandt on 2015-12-15
Note that since you wrote all zeros to it (or at least at the beginning of it even if not complete) it would appear to be an unformatted device with nothing to mount in any OS.

So with gparted, first create a partition table, then add a partition. To be accessible to any OS a memory stick would typically have msdos partition table and a partition formatted FAT32. I had to do that if I would accidentally format the device (like /dev/sdb) instead of the partition on it (/dev/sdb1) in Startup Disk Creator.

---

### Post by Yawanathan_Israel on 2015-12-16
Best thing to do is to re-wipe the usb drive, Wait till it is done, Then format the drive with gparted. Then it should work.



> **Aaronyoman said:**
> Hello everyone earlier today I tried formatting my usb and wiping it entirely. I made it replace everything with full zeros. With no dialogue menu or any GUI screens I decided to take it out thinking maybe it is done. I tried inserting it into my netbook multiple times even after restarting it. Along with a mac and my xbox none could read it. I am running ubuntu 15.10 on cheap Acer aspire one 522 netbook. Please help me

Thanks 
Yawanathan

---

### Post by Bucky Ball on 2015-12-16
> **Yawanathan_Israel said:**
> Best thing to do is to re-wipe the usb drive, Wait till it is done, Then format the drive with gparted. Then it should work.

Thanks 
Yawanathan

Please read all posts from post #3, thanks. This has been suggested, among other things. :)

---

### Post by Aaronyoman on 2015-12-19
its 2 gbs

---

### Post by Aaronyoman on 2015-12-19
Thank you so much I just tried this and added a partition on the usb and it works fine now

---

