---
title: "File transfer between partitions and  w/VMWare virtual machine"
date: 2006-10-12
forum: General Help
---

### Post by ryan^2 on 2006-10-12
I have VMWare up and running and it's pretty functional.  My biggest problem, so far, is the fact that I can't access my Ubuntu or existing Windows 2000 partition.  Any suggestions on how I can make this happen?  I really need the ability to transfer files between partitions and the VMWare virtual machine to make this work for me.

Thanks,

-Ryan

---

### Post by reacocard on 2006-10-12
First, give your virtual machine a host-only networking card. Then set up samba to share files back and forth (just search these forums for a guide, there's tons of them.).

---

### Post by desmondo on 2006-10-12
VMWare Workstation has the capability to share folders from your host to your guest without installing/configuring additional software.

Before you start your Virtual Machine, Edit Virtual Machine Settings.  On the "Options" tab there's an entry for Shared Folders.  Here you can select any of your Linux folders you want to have available in VMWare (for example, I have my home folder selected).

Then, once you start VMWare, in Windows Explorer, go to Tools > Map Network Drive.  The drive is ```
\\.host\Shared Folders
```  Your selected folders will then be available.

Note that you need VMWare tools installed in Windows (but you probably already installed it since VMWare is good about reminding you).

---

### Post by ryan^2 on 2006-10-12
Thanks for the responses.  I have VMWare Server, so went the Samba route using [this]("http://ubuntuforums.org/showthread.php?t=202605&highlight=samba+how-to") how-to.  Looks like it works!!

Thanks again.

---

