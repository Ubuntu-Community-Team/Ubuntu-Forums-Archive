---
title: "HELP! PC booted up empty. Ubuntu 16.04LTS"
date: 2017-03-09
forum: General Help
---

### Post by dtree46 on 2017-03-09
Had no problems with PC last night. Turned it off as usual.

Booted up this am and nothing is the same as before. The home screen has large icons instead of smaller ones.
No sign on screen on. No documents in the document folder, the same for the other folders.
It seems all data, added software and settings are gone.

How does one get this corrected? Grub?
I have the Ubuntu 16.04LTS live disk.

Any help appreciated.
dlw

---

### Post by oldfred on 2017-03-10
Do you have separate /home.
If sounds like your /home did not mount, or is corrupted & it went to a default/new /home.

First run this on all ext4 partitions.
 #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1 

If not run this, just to see configuration.
May be best to see details, you can run from Ubuntu live installer or any working install: 
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

