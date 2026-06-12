---
title: "How to unmount /var - stop respawn"
date: 2012-10-23
forum: General Help
---

### Post by Greg Roberts on 2012-10-23
Hi 
 
I have been trying to copy /var (2nd drive) to a new drive /new_var, content vmware Ubuntu v9.1 vm. 
Goal: Reduce original /var drive size to smaller disk and save 100G. Once working the original /var drive will be deleted.
 
After a lot of struggling, i have the new 3rd drive formatted and has a copy of all the files.
So i am going through the steps given to me below and hit a snag
 
I can't unmount /var 
I stopped samba and am left with atd, cron, rsyslogd with handles on /var (lsof /var)
 
unmount -f does nothing, a kill of the processes achieves nothing because they respawn.
 
>> How do i force the unmount, or force the killed processes NOT to respawn, so i can unmount /var ?
 
"respawn" is not found as a command.
 
cp -fdr /var/* /new_var/
- change the mounting
umount /var
umount /new_var
mount /dev/sdb1 /var
- edit /etc/fstab and adjust it accordingly (i.e. find the '/var' entry and replace the old mount point with /dev/sdb1)
- et voila
 
Thanks

---

### Post by dcstar on 2012-10-24
> **Greg Roberts said:**
> Hi 
 
I have been trying to copy /var (2nd drive) to a new drive /new_var, content vmware Ubuntu v9.1 vm. 
Goal: Reduce original /var drive size to smaller disk and save 100G. Once working the original /var drive will be deleted.
 
After a lot of struggling, i have the new 3rd drive formatted and has a copy of all the files.
So i am going through the steps given to me below and hit a snag
 
I can't unmount /var 
...........

You cannot unmount critical system folders on a running system.

Boot off a Live CD and do whatever you need to, these forums are full of threads detailing the procedure.

---

