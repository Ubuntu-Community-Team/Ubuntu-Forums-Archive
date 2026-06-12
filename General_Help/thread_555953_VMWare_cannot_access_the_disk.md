---
title: "VMWare: cannot access the disk"
date: 2007-09-20
forum: General Help
---

### Post by ZiVvmO on 2007-09-20
I installed vmware player.

read this page: [http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html](http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html)

did what it said (including adding my user to the disk group) and i get:

Cannot open the disk '/home/pj/windows.vmdk' or one of the snapshot disks it depends on.
Reason: Insufficient permission to access file.

any ideas?

---

### Post by benx009 on 2007-09-20
are you running the vmware command as root?

---

### Post by ZiVvmO on 2007-09-20
negative.  im kinda scared to let vmware have root access to my windows partition.

---

### Post by ZiVvmO on 2007-09-20
ok so i sudo'd it and i get bsod error 0x0000007B

---

