---
title: "Dual booting"
date: 2015-09-21
forum: General Help
---

### Post by coors on 2015-09-21
I have or rather had 10.04LTS, 12.04LTS and 14.04LTS along with Vista on my Dell D630.  In Feb I lost 14.04 and in May lost 12.04 and in Aug lost 10.04 and can only boot to Vista.  Using the DVD on boot from DVD none of the  files are visable in any of the Ubuntu versions (partitions).  This week a friend of my mine with same computer lost her files...only has 14.04 on her machine...no dual boot.  Can't take screen shot but will do so with my cell phone.  Any hope of recovering and of the info on either of the laptops?  Any help would be greatly appreciated.
Thanks

---

### Post by oldfred on 2015-09-21
Starts to sound like drive failure. 
Have you checked with Disks, or Disk Utility and Smart Status?

Have you run fsck or made any repairs? Abnormal shutdowns often cause file corruption and you then have to run fsck.

       #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by coffeecat on 2015-09-21
Support, not chat.

*Thread moved to **General Help**.*

---

