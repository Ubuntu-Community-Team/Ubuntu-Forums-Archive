---
title: "cd prompt"
date: 2008-03-17
forum: General Help
---

### Post by coninsan on 2008-03-17
hi 

when i try to install something the message comes up in terminal.

mediachange: insert the disk named
 'Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)'
in drive '/cdrom/' and press enter

how can i disable this, i somehow got it disabled before i formatted due to messed up dual boot. but can remember how.

---

### Post by DoctorMO on 2008-03-17
Edit the sources.list file and comment out the cdrom line right at the top as follows:

```
gtksu gedit /etc/apt/sources.list
```

Then do an update

```
sudo apt-get update
```

Should fix the problem.

---

### Post by PeterJS on 2008-03-17
Go to System > Adminstration > Software Sources and disable the CD-ROM entry down at the bottom.

---

### Post by coninsan on 2008-03-17
WOW that was fast! 

ill give the install another try and se how it goes

---

