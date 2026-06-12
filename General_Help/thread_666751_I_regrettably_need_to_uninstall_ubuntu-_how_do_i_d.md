---
title: "I regrettably need to uninstall ubuntu- how do i do it"
date: 2008-01-13
forum: General Help
---

### Post by ThePigeonKeeper on 2008-01-13
Im very sorry to say i cant keep ubuntu on my computer.  ubuntu is on my second partition but i dont know how to format it please help.

---

### Post by yabbadabbadont on 2008-01-13
Just use the drives manager in Windows to remove and recreate the partition.  Right-click on My Computer and select Manage.

Edit: You'll need to use the fixmbr utility, while booted into the Windows Recovery Console, in order to restore the original Windows MBR.  Do that before you remove the Ubuntu partition, or you won't be able to boot...

---

### Post by devmnky on 2008-01-13
> **ThePigeonKeeper said:**
> Im very sorry to say i cant keep ubuntu on my computer.  ubuntu is on my second partition but i dont know how to format it please help.

This can be easily done as mentioned above, or you can boot your computer with an orginal XP cd, go into the recovery mode, choose the windows installation you use, then type "fixmbr" to restore the Windows XP original master boot record, and then you can reclaim your partition spaces with Windows drive manage tool or GParted.

Hope that helps.

---

### Post by Victormd on 2008-01-13
> **ThePigeonKeeper said:**
> Im very sorry to say i cant keep ubuntu on my computer.  ubuntu is on my second partition but i dont know how to format it please help.

Use the Windows XP Boot CD, that's probably your easiest way...

---

### Post by sporkubus on 2008-01-18
I deleted the Linux partitions and now I need to restore the boot manager without using the Windows XP CD or reinstalling Windows... please tell me there is some other way to do this.

---

### Post by Martin Witte on 2008-01-18
> **sporkubus said:**
> I deleted the Linux partitions and now I need to restore the boot manager without using the Windows XP CD or reinstalling Windows... please tell me there is some other way to do this.
A method I could think of is to install grub, from eg. the system rescue disc [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page), once you can boot again, you can restore the windows bootloader as described before in his thread with the fixmbr utility

---

