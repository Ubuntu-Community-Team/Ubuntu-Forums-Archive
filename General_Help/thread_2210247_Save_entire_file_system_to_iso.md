---
title: "Save entire file system to iso?"
date: 2014-03-09
forum: General Help
---

### Post by Ptomerty on 2014-03-09
Apologize if this is in the wrong place.

I've installed Xubuntu to a flash drive, and I would like to save the whole filesystem to an ISO file in windows.
Is there anyway I can do this, so for example, if I save it to an ISO, would I be able to write it to the flash drive later and boot in?

---

### Post by phidia on 2014-03-09
ALthough remasterssys is not being developed anymore you can still use it. You didn't say what version of xubuntu you are using though.
Check out [this webpage]("http://dondepresso.rujic.net/post/33476896890/how-to-make-a-custom-xubuntu-usb-stick-using-remastersys#.Ux0OONdsiP8") or more info. If you can boot from flash then it should be basically the same as the guide.

---

### Post by Ptomerty on 2014-03-09
12.04.4 LTS, sorry.
So if I backup the entire system to this, I can save it on my computer, write it to another usb stick, and get the exact same system?

---

### Post by phidia on 2014-03-09
That's the ideal. You probably want to test the backup before you are fully confident in that.

---

### Post by raja.genupula on 2014-03-10
[h=2][SIZE=2]Save entire file system to iso : > dd if=/dev/sda1 of=/home/backup.iso
[/SIZE][/h][SIZE=2][/SIZE]

---

### Post by Ptomerty on 2014-03-10
Will the command above be bootable?
E.g., I can write the iso to another usb and boot it?

---

### Post by raja.genupula on 2014-03-10
As you mentioned you want to take the back up ISO , that can help you. But will it boot means that depends what you will backup. but to be frank I never tried that so I dont know.

---

