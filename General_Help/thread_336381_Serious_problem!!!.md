---
title: "Serious problem!!!"
date: 2007-01-11
forum: General Help
---

### Post by moonliter on 2007-01-11
[QUOTE]When I turned on computer today I got this error:

Quote:
GRUB loading, please wait.....

ERROR 17[QUOTE]

so I posted this problem here while trying to resolve byown. It took me 5 hours.So I                  
found somwhere how to fix mbr on xp and now I am running xp again but can't run ubuntu edgy anymore.He is somwhere lost that I can't see.I have all main stuff on ubuntu that don't want to lose,and I really need to back.Please help](*,) ](*,) ](*,) :-k

---

### Post by bodhi.zazen on 2007-01-11
_For access to ext2/3 from windows see_ : [http://www.fs-driver.org/](http://www.fs-driver.org/)

You can also look at the Ubuntu Partition with the live CD and see if it is intact ....

---

### Post by moonliter on 2007-01-11
no this didn't help me it ask me to format partition before open it.I have also installed explore2fs and he also don't see my linux partitions,gparted in live cd  see windows partition and swap partition and for linux says that is unknown

---

### Post by koenn on 2007-01-11
By letting XP repear the boot sector, you've removed some grub boot code an replace it by xp's (Windows is like that). 
If you boot the alternative boot cd (not the Live cd) and do an expert textmode setup, you can find an option to install grub. That will probably fix this, and you can abort the setup routina afterwards. Should work. 

If you have your data (/home) on its own partition, you could also install ubuntu again, making sure you keep the home partition intact (don't format, mountpoint: /home) when going through the partitioning dialog.

---

