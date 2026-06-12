---
title: "Cannot mount NTFS Partition"
date: 2008-04-20
forum: General Help
---

### Post by GCoffee on 2008-04-20
WINDOWS DID NOT SHUTDOWN PROPERLY, RESTARTED AND SHUT DOWN, PROBLEM SOLVED..


Hello,

I wanted to mount my ntfs partition today, but  I cant... whenever i try to it says you are not privileged to mount this volume, I could do it in 7.10 and in 8.04 for a while but now it just wont..

I'm not using any software I'm just using the mount tool in my toolbar..

I think this could have something to do with me messing around in gparted but I didn't actually edit/save anything..

Please Help.

---

### Post by TeoBigusGeekus on 2008-04-20
You do have ntfs-3g and ntfs-config installed, don't you? Check Synaptics if you are not sure.
Then go to applications->system tools->ntfs configuration tool
check your drive and check all the write support buttons. 
I hope this helps...

---

### Post by vanadium on 2008-04-20
Is this an internal or an external drive? What is the precise error message?

For permanent drives, only root has the right to mount. Removable drives are mounted automatically when you connect them.

One frequently occurring problem with ntfs for dual boot users is that the drive was not properly disconnected in Windows. You shoudl provide more information. For disk related problems, it is also a good idea to post the output here of "sudo fdisk -l" and "mount".

---

### Post by GCoffee on 2008-04-20
I have ntfs-3g installed but not a link to it in the menu...

---

### Post by TeoBigusGeekus on 2008-04-20
Install ntfs-config as well and follow my first post.

---

### Post by twin_57103 on 2008-04-20
> **vanadium said:**
> 
One frequently occurring problem with ntfs for dual boot users is that the drive was not properly disconnected in Windows.

I've encountered this a couple times if Windows crashes rather than shuts down properly.  If there was a Windows crash, you can often resolve the problem by rebooting Windows, then shutting it down normally and rebooting to Ubuntu.

---

### Post by magiceraser06 on 2008-05-07
I have the same issue.  Now, how would one go about fixing this issue without a windows installation?

I have already deleted and installed Ubuntu over the windows drive.  Is there anyway to mount my other NTFS partition through Ubuntu? None of the known fixes work for me.

Also, windows XP doesn't like more than three partitions. I tricked it into doing four, so that could also be something on my end.

any help?

cheers.

---

