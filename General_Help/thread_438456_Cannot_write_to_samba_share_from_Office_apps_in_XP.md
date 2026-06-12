---
title: "Cannot write to samba share from Office apps in XP guest (Linux host)"
date: 2007-05-09
forum: General Help
---

### Post by galileux on 2007-05-09
I run Workstation 6 Beta 44426 on Ubuntu_7.04-64 host and an XP guest.
Hardware is Core2Duo with 4 GB Ram.

I do not use Workstation's share folders, instead, I have a separate fileserver running Ubuntu-server 6.10, Samba, and a number of shared disks.

- I can access, read, write and execute on all samba shares from a separate XP client (non-vmware).

- I read, write, execute on all samba shares from the Linux host.

- From the WS XP guest, I can read, write and execute and create new files (e.g. with notepad) on the samba shares.

THE PROBLEM: when I try to create new files o modify using OFFICE APPLICATIONS from the XP guest, I get various messages and the writes fail.

Example of message from Word:

"The save failed due to out of memory or disk space (SAMBASHARE:\Path\file.doc)"

Example of message from windows appearing in the warning area of the taskbar:

"Windows - Delayed Write Failed
Windows was unable to save all the data for the file \\Network_path\. The data has been lost. This error may be caused by a failure of your computer hardware or network connection. Please try to save this file elsewhere."

I checked the router and DHCP server and made sure the VM has its own static address.
Checked the permissions, they should be ok.
This happens ONLY from the Workstation client, and ONLY with Office apps.

Can anyone help?
Thanks

---

### Post by galileux on 2007-05-17
That is now resolved.
If you need the solution, pls check this thread:

[http://ubuntuforums.org/showthread.php?t=439497](http://ubuntuforums.org/showthread.php?t=439497)

---

