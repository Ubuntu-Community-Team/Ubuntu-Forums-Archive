---
title: "Windows Disapeared From Grub"
date: 2015-12-26
forum: General Help
---

### Post by Darth4212 on 2015-12-26
I am currently running Ubuntu 15.10 and was dual-booting with Windows 10 I started up my computer to find Windows missing from the Grub selection list what happened. I haven't messed with the partition that Windows is on why did it disappear?

---

### Post by oldfred on 2015-12-26
Did a Windows update turn its fast start up back on or does it need chkdsk?
Then a grub update could not see the Windows NTFS boot files and removed entry from grub menu?

Check Windows settings, if that does not solve issue run Boot-Repair's summary report & post link.
       [https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by Darth4212 on 2015-12-27
I can't check windows boot settings because I can't even access windows

---

### Post by yancek on 2015-12-27
> I can't check windows boot settings because I can't even access windows 		

Then run the boot repair suggested above and post the output here.

---

### Post by Darth4212 on 2015-12-28
Sorry for the trouble I had installed GRUB customizer and someone got ahold of my computer and somehow hid the Windows entry. I need to put a better password and make sure no one sees me when I am typing it.

---

