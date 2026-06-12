---
title: "Eliminating old boot partition ?"
date: 2016-02-22
forum: General Help
---

### Post by ra7411 on 2016-02-22
I was having some problems I couldn't fix in Ub 15.10, so I wound up doing a side by side install of a new Ub 15.10 (sda6).

Everything went fine, the new install seems good, and I changed the old boot partition (sda1) to "unallocated" in Gparted.

When I started the process to expand my separate /home partition (sda3) to take over the unallocated old boot partition, Gparted gave a warning that it might screw up the boot process - something I don't want.

How do I handle this? Leave well enough alone? Go ahead and expand the start of sda3 to take over the unallocated space and don't worry about it?  Reformat the unallocated space and install some other Ub versions for fun?

Gparted pic attached.

---

### Post by yancek on 2016-02-22
Have you rebooted your new Ubuntu install since changing the old boot partition to unallocated?
Do you have the standard boot files for Grub on the sda6 partition and did you install Grub code to the MBR with the new install on sda6.
If the answers are yes, it shouldn't be a problem.  A 185GB boot partition??

---

### Post by Rocky_Bennett on 2016-02-23
To touch on what yancek has said, I believe that even if you are not dual booting you should still run a command from your new Ubuntu installation to update the Grub boot loader. This is always a good idea when you muck around with partitions. Also, I can not emphasize enough, back up any important data that you might have on sda3. This is always a safety precaution "JUST IN CASE." You could back that data up to a desk top hard drive, but definitely back it up before you mess around with your partitions.

Another thing that yancek had touched on that I totally agree with is the size of your boot partition. It is ridiculously large. You could shrink that to about 40 to 60 gb and still be safe. If that was my system I would not eliminate the unallocated partition, I would simply format it to ext4 and let it sit there until April when Ubuntu 16.04 comes out. Then I would use that partition to install Ubuntu 16.04 on and mess around with that while you still have a clean install of Ubuntu 15.10 on your main partition. That way you can upgrade to Ubuntu 16.04 when it is brand new with out taking the chance of having a borked system.

At this point you have a lot of options. 

Rocky Bennett

---

### Post by yancek on 2016-02-23
Given the abnormally huge size of the former boot partition, simply creating another partition and formatting it to use as a data partition would probably be simpler and also safer.  Moving the home partition is also moving the data in the situation above.  I think 1GB is a realistic size for a boot partition and for new users, it is a lot simpler not to have a separate boot partition.  Years ago, with older hard drives it might have been necessary.  There are still valid reasons to use a boot partition but for normal home users, especially new users, it's an unnecessary complication.

---

### Post by ra7411 on 2016-02-23
I updated Grub, rebooted, and to my amazement all went well. I formatted the old o/s 200gb partition and will leave it alone until Ub 16 comes out. I have 3Tb HD space on this system and only use 1+Tb including backup, so space is no constraint.

---

