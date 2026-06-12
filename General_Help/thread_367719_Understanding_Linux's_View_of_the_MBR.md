---
title: "Understanding Linux's View of the MBR"
date: 2007-02-22
forum: General Help
---

### Post by mgorsuch on 2007-02-22
Hello everyone.  I've decide to move my organization onto the Ubuntu server platform, and have been working out a quick deployment method using DD.

I noticed something today, and am hoping that some of you can shine some light on this.  I'm not asking for a solution, just an understand of how this mechanism works. 

If I boot a computer up with an empty disk and dd a backed up MBR, I cannot successfully restore my old partitions via DD without a reboot first.  The dd fails with a 'not enough free space on device' error.  

But, as I stated, after a reboot, all is well.  I am *assuming* that the kernel learns about it's partitions upon boot after reading the mbr.  Is this a correct assumption?  Are there any tricks to get it to 'reload' it's understanding of the layout?  

For what it's worth, this is all happening on a Dell 2850 with a Perc 4e/di RAID controller.

I'll live with the reboot, I just want to make sure that I have thought everything through. 

Thanks!

---

### Post by boredandblogging.com on 2007-02-22
[How Boot Loaders Work]("http://www.xs4all.nl/%7Elennartb/bootloaders/node3.html")

---

