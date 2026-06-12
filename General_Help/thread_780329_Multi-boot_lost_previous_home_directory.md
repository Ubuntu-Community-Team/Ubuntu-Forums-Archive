---
title: "Multi-boot lost previous /home directory"
date: 2008-05-03
forum: General Help
---

### Post by DaddyX3 on 2008-05-03
I have run into some problems with Ubuntu Hardy Heron 8.04 both on 32 and 64 bit versions. Upon install I selected "manual" and partitioned off a seperate /home directory partition as well as a /backup or /whatever partition. Durring the install, (32-bit version) it asked me if I wanted to import settings from another account (my Ultimate Edititon). I ticked "yes" to import them. The install went through with no problem and 8.04 ran just fine. However, Somehow it actually removed my /home/my_user_name folder right out of existence on my other distro!!!! I couldn't believe it. I mounted my other partition from within Ubuntu and low and behold .. no user folder on the /home partition of that distro anymore!! Not a big deal, I'm good at little problems like this. However, I also have had this problem with the 64-bit edition of Ubuntu as well. I installed using the same exact method (manual install) only this time I did not import settings from another account. This time again- it scrambled my partitions around in the other distro's and can not find the /home partitions. I have had to go back in and do a sudo nano /etc/fstab and re-associate my /home partitions with each distro. Now on both 32 and 64 bit versions it does not fully boot without dropping me into a command line stating that my external /dev/sde could not mount (this happens to be a eSATA drive) I then have to cntrl+D to continue with boot. Does anyone else have this problem or no of a solution?

---

