---
title: "Cant Eject Cd!"
date: 2007-11-12
forum: General Help
---

### Post by Spaazkaz on 2007-11-12
Ive been browsing and browsing the hlp forum here, no luck. I dont know what im doing got sick of windows a couple days ago and threw in ubuntu to give it a try and im trying to adjust... bear with me. I have an iso on a cd and I want to freakin take it out of my drive because its not doing what i want in the drive. Initially it the autoexec file started up but after i closed it the first time I cant get the drive to pop out... I get there errors. 

zack@cpe-69-202-95-113:~$  sudo eject /media/cdrom0
umount: /media/cdrom0: device is busy
umount: /media/cdrom0: device is busy
eject: unmount of `/dev/hdc' failed
zack@cpe-69-202-95-113:~$ umount /dev/hdc
umount: /media/cdrom0: device is busy
umount: /media/cdrom0: device is busy
zack@cpe-69-202-95-113:~$


what to do. any help is appreciated.

-Zack-

---

### Post by reckless2k2 on 2007-11-12
hard shutdown your machine by holding down the power button. the cycle it up again but push the eject button as soon as it starts. i strangely get this sometimes too where i can eject a CD.

---

### Post by anliveyak on 2007-11-12
you can turn off the computer and reboot or in terminal type "top" and find the process that is using the disk then ill the process

---

### Post by Spaazkaz on 2007-11-12
damn the support from users makes this OS worth the [intial] trouble. Thanks so much. Can you guys give me any links that might give me a tutorial on the basics of linux or more specifically ubuntu? thanks again

---

### Post by anliveyak on 2007-11-12
the tour for unubtu gusty "http://www.ubuntu.com/getubuntu/releasenotes/710tour"

---

