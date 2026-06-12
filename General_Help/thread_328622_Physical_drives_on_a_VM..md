---
title: "Physical drives on a VM.?"
date: 2006-12-31
forum: General Help
---

### Post by ashmew2 on 2006-12-31
Hi everyone 
I m currently using Dapper Drake (32 Bit) and I have installed Vmware Workstation 5.5.2 build-29772. I have made a Virtual Machine and installed XP on it as some things i love wont work on Ubuntu. Anyways , is there a way I can mount my physical drives inside the Virtual Machine (with read and write capabilities). These drives are mounted under Ubuntu at mount points "/media/hda1" , "/media/hda5" and "/media/hda/6". Thanks.

---

### Post by rbalfour on 2006-12-31
You can install the VMware tools and create shared folders to access /media/* drives with R/W access.

---

