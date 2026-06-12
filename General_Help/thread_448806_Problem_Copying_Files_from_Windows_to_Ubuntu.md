---
title: "Problem Copying Files from Windows to Ubuntu"
date: 2007-05-19
forum: General Help
---

### Post by JoeyMan on 2007-05-19
Hi, recently, my Windows crashed and I was unable to access Windows and all the files it help, so I decided to install Ubuntu and try to access all the files and copy them to Ubuntu. I don't need to write to any of the files, just copy them over. I installed Ubuntu and followed the guide listed here: [http://ubuntuguide.org/wiki/Dapper#How_to_mount.2Funmount_Windows_partitions_.28NTFS.29_manually.2C_and_allow_all_users_to_read_only]("http://ubuntuguide.org/wiki/Dapper#How_to_mount.2Funmount_Windows_partitions_.28NTFS.29_manually.2C_and_allow_all_users_to_read_only") but I reached a problem.

No errors came up or anything, but when I goto the drive that is mounted, I see no files! It says the proper size of the partition, about 67 gigs, but it says there are 0 files there. Is there a way to fix this or are all my files on my windows partition lost forever? Is there some place I can go to check and see how much space is being used on my Windows partition to verify that there is still indeed files on there? Thank you.

---

### Post by TheWizzard on 2007-05-19
are you sure you didn't format the drive with windows files?

---

### Post by rsambuca on 2007-05-19
Can you post the output of your fstab so we can have a look?  Open a terminal (Applications -> Accessories -> Terminal) and enter the following command:```
cat /etc/fstab
```Copy and paste the output here and we should be able to help you out.

---

### Post by octoberdan on 2007-05-19
> **rsambuca said:**
> Can you post the output of your fstab so we can have a look?  Open a terminal (Applications -> Accessories -> Terminal) and enter the following command:```
cat /etc/fstab
```Copy and paste the output here and we should be able to help you out.

and the output of ```
 mount 
```

---

