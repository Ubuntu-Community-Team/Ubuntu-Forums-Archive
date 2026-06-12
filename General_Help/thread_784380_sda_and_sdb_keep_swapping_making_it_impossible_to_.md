---
title: "sda and sdb keep swapping making it impossible to boot"
date: 2008-05-06
forum: General Help
---

### Post by harty83 on 2008-05-06
I have hardy 8.10.  Upgraded some packages this morning and restarted the computer.  Now, I cannot boot up.  I get 

> fsck.ext3: Bad magic number in super-block while trying to open /dev/sdb1
dev/sdb1: The superblock could not be read or does not describe a correct ext2 filesystem.
Blah blah blah
/

Well it fails because /dev/sdb1 is not a ext2 but a NTFS filesystem with windows vista installed on it.  Somehow, my drives got swapped (sda<->sdb).  So went into fstab, switched everything, and rebooted to find that it booted them swapped again so the same issue!  Almost every time I reboot after editing fstab, sda and sdb swap thus giving the error above because it thinks the ntfs filesystem is an ext3.  I was able to boot once, but x was not loading correctly but as soon as I rebooted, same issue.  WTF?!  

Any ideas?

---

### Post by bingoUV on 2008-05-06
> **harty83 said:**
> I have hardy 8.10.  Upgraded some packages this morning and restarted the computer.  Now, I cannot boot up.  I get 



Well it fails because /dev/sdb1 is not a ext2 but a NTFS filesystem with windows vista installed on it.  Somehow, my drives got swapped (sda<->sdb).  So went into fstab, switched everything, and rebooted to find that it booted them swapped again so the same issue!  Almost every time I reboot after editing fstab, sda and sdb swap thus giving the error above because it thinks the ntfs filesystem is an ext3.  I was able to boot once, but x was not loading correctly but as soon as I rebooted, same issue.  WTF?!  

Any ideas?

 Why don't you use UUID in fstab to prevent this? If in doubt, post the contents of your /etc/fstab and the output of the following command : ```
 ls -l  /dev/disk/by-uuid 
```

---

### Post by harty83 on 2008-05-06
Ah, thanks.  They originally were by the UUID except for one which caused the problem to begin with.  I found the UUID using your command and then changed them ALL to the UUID and now I boot up.

BUT, now nvidia seems to be jacked up. I cannot get a display with a resolution greater than 800x600 (I have a 1440x900 widescreen).  I cannot enable the nvidia driver.  I have it installed with the restricted modules.  I go into System -> Administration -> Hardware Drivers but nothing is listed there.  I try activating it using displayconfig-gtk but nothing works and or x crashes.  I've tried purging nvidia everything, cleaning the cache, and reinstalling to no avail.  Any ideas on that?

Thanks!
Alan

---

### Post by bingoUV on 2008-05-07
I stay miles away from nvidia so I have no clue. A new thread with appropriate topic should help you.

---

