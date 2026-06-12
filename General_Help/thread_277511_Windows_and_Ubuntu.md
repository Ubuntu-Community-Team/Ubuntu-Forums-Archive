---
title: "Windows and Ubuntu"
date: 2006-10-14
forum: General Help
---

### Post by FleetAdmiral74 on 2006-10-14
Do Windows and Ubuntu work well when on the same HD? I have read some articles saying they basicly rape eachothers MBRs upon install, often without user notification.

My bro has his comp with one HD all windows, but he has lots of free space. Can he safely set up Ubuntu using some of the free space without messing up his Windows partition?

---

### Post by taurus on 2006-10-14
Yes, you can install both Windows and Ubuntu on a same harddrive.  Just make sure you have an empty partition for Ubuntu.  If you don't have one, you can use gparted which is available on the desktop CD (LiveCD) to resize your harddrive...  Then, you would want to install GRUB on MBR so it can boot both Windows and Ubuntu.

---

