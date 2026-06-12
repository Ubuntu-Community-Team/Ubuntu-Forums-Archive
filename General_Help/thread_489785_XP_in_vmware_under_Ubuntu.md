---
title: "XP in vmware under Ubuntu"
date: 2007-07-01
forum: General Help
---

### Post by geekphreak on 2007-07-01
I have a question about setting up XP in vmware under Ubuntu: if I install vmware tools, will XP VM be able to see Ubuntu's partitions and write to them? I would like to have a partition with all docs and data that Ubuntu and XP VM could both use, read and write to it. Is that possible? Which filesystem should I use for that partition?
Thanks!

---

### Post by mikewhatever on 2007-07-01
No, don't think so. The VM can't see outside its virtual disk, but, perhaps you can use some removable storage.

---

### Post by fjf on 2007-07-01
You should try Virtualbox. The free version 1.4 allows sharing folders between the host and the virtual machine. To do that with vmware will make you purchase the workstation version and spend $180. Go to the virtualbox web and click on the *.deb file provided there for feisty. Easy.

---

### Post by geekphreak on 2007-07-01
> **fjf said:**
> You should try Virtualbox. The free version 1.4 allows sharing folders between the host and the virtual machine. To do that with vmware will make you purchase the workstation version and spend $180. Go to the virtualbox web and click on the *.deb file provided there for feisty. Easy.

OK, I have used VirtualBox before, but what I could not figure out was the sharing part. Have you tried sharing a Feisty partition with Windows VirtualBox machine? I do not want to redo my installation until I know it is doable. Thanks!

---

### Post by PilotJLR on 2007-07-01
Just export the ubuntu directories with Samba, and mount it as a drive letter in the XP guest...

---

### Post by Anzan on 2007-07-01
For a cheap and easy fix, when I was using Ubuntu in VMplayer on Vista I just sent files to myself in Gmail or used the Gspace extension in Firefox.

---

### Post by scxtt on 2007-07-01
i use samba + nfs b/t an XP VM and my Kubuntu/Gentoo physical hosts ...

---

