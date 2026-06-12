---
title: "[SOLVED] Removing Ubuntu?"
date: 2008-06-26
forum: General Help
---

### Post by Landscapeman on 2008-06-26
I have a friend with a Toshiba Sat. M65 running ubuntu and is giving the computer away. It originally had Windows XP and I need to reinstall windows for the new user, They need Microsoft Publisher and Quickbooks. How do I go about it. I used the restore cd from Toshiba and all it did was gave me error 77 for grub. Any ideas that would completely remove the ubuntu so I can reinstall windows.

---

### Post by Rocket2DMn on 2008-06-26
You should be able to boot from the Windows XP disc by changing the BIOS boot order to put the cdrom drive ahead of the hard drive.  Then you can delete the existing partitions from there and install Windows.  It will then take over the MBR so GRUB is gone.

---

### Post by Landscapeman on 2008-06-26
Windows Home wouldn't do it so I decided to use Pro and it worked fine. Thanks for the respone.

---

