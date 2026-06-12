---
title: "Help with some couple problem in KUBUNTU"
date: 2017-09-17
forum: General Help
---

### Post by alexandr-lamdan on 2017-09-17
**First problem:**
I install the Kubuntu 17.04 on my SSD its a system drive  and named /dev/sda.
And i have my second drive,but not mount automaticly is the HDD with 4 TB. In that second drive i have developer projects,music, and the another stuff.
So how can i mount my second drive who named with /dev/sdb1 to /media/alexandr_lamdan/F(its will be a Label of my second drive) with all permissions and read,write and changing,but i need to make it that automatic mount.

**Second problem:**
I install the apache2 and all stuff with that. But when i try to opened php file or html file in apache, its giving me a Forbbiden error or the access denied error. I try to change directory root, i try to make it in another folder, and its not work. example: directoryRoot /media/alexandr_lamdan/F/alexandr_php_mysql THAT NOT WORKING .Its giving me a error to access denied all the time.

---

### Post by oldos2er on 2017-09-17
To automount a partition you need to add it to your /etc/fstab file. See [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

