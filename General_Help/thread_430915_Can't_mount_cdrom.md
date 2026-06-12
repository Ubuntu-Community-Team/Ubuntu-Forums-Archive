---
title: "Can't mount cdrom"
date: 2007-05-02
forum: General Help
---

### Post by 999alfred on 2007-05-02
I cannot mount a cdrom under edgy. It gives an error
Special device /dev/hdc does not exist.
And sure enough /dev/hdc DOES NOT EXIST and MAKEDEV does not create it.

I can plug in a memory card using a usb adapter and it gets automatically mounted ok.

So, how the heck fo I get the dvd rom drive to mount? Kind of a useless system with out cdrom/dvd drives working.

tj

---

### Post by apunc1 on 2007-05-02
if you open up nautilus and click on the computer icon at the top to display the drives, can you see the cdrom drive? can you see it in /media?

---

### Post by 999alfred on 2007-05-02
I found my problem as to why I could not mount the cdrom. 
I boot either Slackware, Windows or Ubuntu using lilo. In the lilo config file I used had
  append="hdc=ide-scsi hdd=ide-scsi"
(I block copied the section form the slackware boot section.
 But, I had no module rule to use scsi for ide.
Duh, that ain't going to work.

The tell tale was the boot messages having
ide_setup: hdc-ide-scsi
But, cdrecord -scanbus listed no cdroms.

Removing the append command from the lilo.conf  Ubuntu section solved the problem.

tj

---

