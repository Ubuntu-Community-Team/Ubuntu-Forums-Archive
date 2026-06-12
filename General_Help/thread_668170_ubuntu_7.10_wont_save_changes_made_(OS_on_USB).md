---
title: "ubuntu 7.10 wont save changes made (OS on USB)"
date: 2008-01-15
forum: General Help
---

### Post by quickshot89 on 2008-01-15
right, i followed the method on pendrivelinux.com to get my 7.10 on a 1gig usb stick

everything works fine, i can boot into persisantce mode

but when i make changes, turn the computer down, and when i reboot, my changes arnt saved

any help to get this sorted?

---

### Post by r-mo on 2008-01-15
Sounds a bit like it's not able to write to the data partition.  Try booting back into the live cd environment (or an installed one) insert the usb and see if there's anything on the casper-rw partition.  Also,  try writing a file to it.
```
sudo touch /media/casper-rw/tst
```

---

### Post by quickshot89 on 2008-01-19
sorry for long reply, i reinstalled ubuntu 7.10 again, and did a test at the end of the installation, the file was written to the casper file, booting back up onto the usb so will edit this post if it still doesnt work

---

