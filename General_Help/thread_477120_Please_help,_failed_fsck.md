---
title: "Please help, failed fsck"
date: 2007-06-18
forum: General Help
---

### Post by forevereating on 2007-06-18
Hello everybody. I feel a bit stressed out right now, Why? Because I tried to make a ext3 partition into ntfs with GParted, but it wouldn't let me without complications. So I compromised and choose fat32 which should still let me share files between windows and ubuntu. And it worked, so I restarted to double check. Then it tells me it failed one of the fsck test on the partition I just changed. Now I've changed it back to ext3, knowing that it probably won't fix the problem, and it doesn't. So I need help fixing it, I don't even know whats wrong though, it just tells me it failed the test. And I have to mount the partition manually, how can I make it do it automatically again?

---

### Post by mcduck on 2007-06-18
> **forevereating said:**
> Hello everybody. I feel a bit stressed out right now, Why? Because I tried to make a ext3 partition into ntfs with GParted, but it wouldn't let me without complications. So I compromised and choose fat32 which should still let me share files between windows and ubuntu. And it worked, so I restarted to double check. Then it tells me it failed one of the fsck test on the partition I just changed. Now I've changed it back to ext3, knowing that it probably won't fix the problem, and it doesn't. So I need help fixing it, I don't even know whats wrong though, it just tells me it failed the test. And I have to mount the partition manually, how can I make it do it automatically again?

Find the right UUID for your partition with 'ls -la /dev/disk/by-uuid' and then edit your /etc/fstab to use correct UUID. Formatting a partition will also change it's UUID so you need to do this afterwards. (Also, if you change the file system you of course need to change fstab to use correct file system for the parttion).

---

### Post by forevereating on 2007-06-18
Ok, so I did what you said, and it doesn't give me the failed message at boot anymore (thanks). However I can't read or write into it. If I run as root I can view it, but since it is mounted as read only I still can't write. How would I mount it with read/write permissions for my account? Oh, btw the filesystem is now ntfs. Thanks again.

---

### Post by mcduck on 2007-06-18
> **forevereating said:**
> Ok, so I did what you said, and it doesn't give me the failed message at boot anymore (thanks). However I can't read or write into it. If I run as root I can view it, but since it is mounted as read only I still can't write. How would I mount it with read/write permissions for my account? Oh, btw the filesystem is now ntfs. Thanks again.
Linux doesn't natively support writing to NTFS as it's Microsoft's proprietary file system. But there's NTFS driver in Ubuntu repositories and that allows you to mount NTFS drives in read/write mode. Try searching the forum for 'ntfs-3g' (I can't help with that as I have never used it).

---

### Post by forevereating on 2007-06-19
AH HA! Finally got it fixed with write permissions into ntfs. Thanks a lot mcduck.

---

