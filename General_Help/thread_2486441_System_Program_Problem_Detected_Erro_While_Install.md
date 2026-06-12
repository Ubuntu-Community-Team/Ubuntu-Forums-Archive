---
title: "System Program Problem Detected Erro While Installing Ubuntu 23.04"
date: 2023-04-30
forum: General Help
---

### Post by anychare on 2023-04-30
I have been battling to install Ubuntu 23.04 on a PC with Windows 10 already. I chose the option to install Ubuntu along Windows 10 but I continuously get the error that says 'System Program Problem Detected' and the installation does not go through. Even when I try the option to do a manual disk partitioning after shrinking my Windows 10 partition I get the same error. See screenshot attached. How can I get to install Ubuntu 23.04 smoothly. I have been at it for the whole day but failing.

---

### Post by ActionParsnip on 2023-04-30
I suggest you resize the NTFS in Windows if you haven't already. Once you have unallocated space, reboot the PC and run a full chkdsk to make sure the NTFS is complete and consistent. Then shutdown the system (not reboot or suspend).
Then boot to the install media, it should help

---

