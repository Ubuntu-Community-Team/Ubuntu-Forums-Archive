---
title: "[SOLVED] Blanking a CDRW"
date: 2007-10-07
forum: General Help
---

### Post by IanB2 on 2007-10-07
I hope you can help

I have managed to write data to a CDRW using Gnomebaker but seem unable to then delete the  CDRW. I have also tried the same process with Xfburn with the same results.

Each time the written CDRW seems to behave like a CDROM. I then have to use windows (nero) to erase the CDRW. Why can't I do this in Linux?

Thanks in anticipation.

---

### Post by coffeecat on 2007-10-07
Have you tried Tools > Blank CDRW in Gnomebaker? Does this work?

Afterthought - K3b is a more versatile CD/DVD application, and I usually choose this to re-format CDRWs. Have you tried that? The only disadvantage when you are using the Gnome desktop is that K3b is a KDE app and if you install it, it will drag a load of KDE dependencies in with it.

---

### Post by IanB2 on 2007-10-07
Thanks .... I have tried the 'blank CD' function in both GnomeBaker and Xfburn both of which refuse to work on my copy of Ubuntu 7.04

The written CDRW appears on the desktop but seems to behave like a CDROM. Error messages seem to suggest that programs beleive that the CDRW is now a CDROM, once data has been written on the first occasion. I'm also unable to burn any further data onto the CDRW.

Any ideas before I try another program?

---

### Post by IanB2 on 2007-10-07
This is the error message I get in Xfburn

scsidev: '/dev/sr0'
devname: '/dev/sr0'
scsibus: -2 target: -2 lun: -2
Error trying to open /dev/sr0 exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/sr0 exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/sr0 exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/sr0 exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/sr0 exclusively (Device or resource busy)... giving up.
TOC Type: 1 = CD-ROM

Can anyone help? 
I used Xfburn to initially write data to the CDRW.

---

### Post by IanB2 on 2007-10-31
I believe that the problems are hardware related to the laptop that I'm using.

I'm managing to burn CDs & CDRWs on my dual boot desktop with no problems.

---

### Post by Maestro23 on 2007-10-31
> **IanB2 said:**
> I believe that the problems are hardware related to the laptop that I'm using.

I'm managing to burn CDs & CDRWs on my dual boot desktop with no problems.

Have you  looked to see if there is a firmware update for your hardware?

---

### Post by IanB2 on 2008-05-29
Thanks for your help ..... I've not been able to find a firmware update but I can blank CDRWs on my windows box.

---

