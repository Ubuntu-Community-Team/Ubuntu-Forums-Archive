---
title: "Unable to Boot error on startup"
date: 2019-08-11
forum: General Help
---

### Post by ripeamado on 2019-08-11
I got this problem too...
I installed ubuntu 18.04 some time ago and after a long time using it   the other day give me this problem. Now it's impossible to boot ubuntu. I   have installed the latest version (19.04) and it's too not working,  the  same error.
I tried too to change the BIOS disbling Security Boot but nothing happen....
Windows 10 boot normally.
I need a solution, please!

---

### Post by oldfred on 2019-08-11
Moved to your own thread, since other thread is older.
Only for reference, older thread:
[https://ubuntuforums.org/showthread.php?t=2410301](https://ubuntuforums.org/showthread.php?t=2410301)

What brand/model system?
Are you booting directly from UEFI? Or a default boot entry.

Often a grub version issue.
       MODSIGN: Couldn't get UEFI db list
From different grub install error.
[https://bugzilla.redhat.com/show_bug.cgi?id=1497559](https://bugzilla.redhat.com/show_bug.cgi?id=1497559)
Change UEFI settings from custom to standard
[https://ubuntuforums.org/showthread.php?t=2380700](https://ubuntuforums.org/showthread.php?t=2380700)
[https://ubuntuforums.org/showthread.php?t=2407705](https://ubuntuforums.org/showthread.php?t=2407705) 
    
       May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) &

---

