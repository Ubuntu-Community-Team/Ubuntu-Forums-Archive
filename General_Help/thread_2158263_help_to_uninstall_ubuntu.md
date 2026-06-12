---
title: "help to uninstall ubuntu"
date: 2013-06-28
forum: General Help
---

### Post by reptile1 on 2013-06-28
permission denied on using control panel in xp to uninstall ubuntu. have xp/ ubuntu dual boot. dont know how ubuntu was added to dual boot.
have main disk c 2 partitions 1 primary ntfs 127gb and 1 unallocated ntfs 337gb. want to remove ubuntu and merge both partitions.
how do I proceed as c drive only 4gb left to use

Thanks
Paul

---

### Post by grahammechanical on 2013-06-28
You are confusing me. If Ubuntu was installed to the hard disk as a true dual boot then there would be more than two partitions. The Ubuntu install would have added two partitions just for Ubuntu. One for Ubuntu and one for swap.

I am guessing that you installed Ubuntu using Wubi.exe. This only gives the impression of there being a dual boot. Ubuntu is installed and removed just as any other Windows application is. Do you need administrator privileges to Add and Remove programs in XP?

What partition is Ubuntu on? If you use a Windows utility to delete one partition and then to resize the other partition, you will lose anything that is on the deleted partition. If that is Ubuntu and you do not mind loosing it, then remove Ubuntu that way but you will still have it as a boot option. You may have to restore Windows to the MBR.

You could use BOOT Repair. That also has a OS un-installer tool

[https://help.ubuntu.com/community/OS-Uninstaller](https://help.ubuntu.com/community/OS-Uninstaller)

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

For a Wubi install this may help

[https://wiki.ubuntu.com/WubiGuide/#How_do_I_uninstall_Wubi.3F](https://wiki.ubuntu.com/WubiGuide/#How_do_I_uninstall_Wubi.3F)

Regards.

---

