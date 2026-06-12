---
title: "help: dvd drive not working"
date: 2006-08-18
forum: General Help
---

### Post by greglee on 2006-08-18
hi friends
I need help on my optical drive. ](*,) 

After installation of Ubuntu 6.06, there is a DVDR drive appearing in the Places->Computer.  However, every discs that I load in appeared as a blank disc.  If I load a CD (any type), it shows blank CD; if I load a DVD (any type) is shows a blank DVD.

Everything else checks out fine, the drive is properly mounted (as far as I can tell), I can eject and close the tray...

Any help will be appreciated, thanks.

---

### Post by DoctorMO on 2006-08-18
Do you mean the folder which the CD/DVD is mounted to is blank or that the Icon and name of the CD that apears on the desktop is 'Blank CD'?

What kind of Optical Drive do you have?

---

### Post by greglee on 2006-08-19
Yes, the folder is blank, and the name is also "Blank CD' or "Blank DVD".

I have a DVD+RW drive.

---

### Post by DoctorMO on 2006-08-22
hmm, sounds like a hardware dettection fault, possibly in HAL or G-V-M problem in relation to the optical drive.

I don't think there is much we can do to help. you can try mounting the drive manualy:

[http://ubuntuguide.org/wiki/Dapper#How_to_mount.2Funmount_CD.2FDVD-ROM_manually.2C_and_show_all_hidden_and_associated_files.2Ffolders](http://ubuntuguide.org/wiki/Dapper#How_to_mount.2Funmount_CD.2FDVD-ROM_manually.2C_and_show_all_hidden_and_associated_files.2Ffolders)

---

### Post by greglee on 2006-08-23
hi DoctorMO
Thanks!  It is now partially working.  I tried the commands in the page you provided:

$ sudo umount /media/cdrom0/
umount: /media/cdrom0/: not mounted

I think this means the auto-mount is not working.  Then:

$ sudo mount /media/cdrom0/

The Computer-> DVD-RW still shows blank disc, but /media/cdrom0 now has the disc contents.

Any idea what is broken, and how to fix?  Thanks.

---

