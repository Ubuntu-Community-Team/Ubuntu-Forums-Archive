---
title: "Copying win-files with æ ø å"
date: 2006-07-25
forum: General Help
---

### Post by SwedChef on 2006-07-25
Hi!

I'm using kubuntu live to salvage photos from a laptop with dying harddrive (previous OS was windows). Even though i am quite new to Linux, i am using console to get root access (sudo command) - and it's working great with one exception - I can't copy files with æ, ø or å - The letters in the filename is replaced by "?" and i have tried a few different things with no luck - How do i copy these files?

Kind Regards,
SwedChef

PS - Sorry for the bad english..

---

### Post by Ares Drake on 2006-07-25
you have to change the way you mount the windows partitions. you either have to add the following to your mount command or to your fstab file:

nls=utf8 for ntfs
iocharset=utf8 for fat(32)

for details see: [http://doc.gwos.org/index.php/DapperGuide#How_to_mount.2Funmount_Windows_partitions_.28NTFS.29_manually.2C_and_allow_all_users_to_read_only](http://doc.gwos.org/index.php/DapperGuide#How_to_mount.2Funmount_Windows_partitions_.28NTFS.29_manually.2C_and_allow_all_users_to_read_only)

have fun!

---

### Post by SwedChef on 2006-07-25
Thanks!

That surely saved her day! (and more!)

---

### Post by Ares Drake on 2006-07-26
I'm glad that I could be of some help :)

---

