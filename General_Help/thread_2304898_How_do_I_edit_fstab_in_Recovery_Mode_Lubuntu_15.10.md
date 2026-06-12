---
title: "How do I edit fstab in Recovery Mode Lubuntu 15.10?"
date: 2015-12-01
forum: General Help
---

### Post by roler2 on 2015-12-01
I added some tweaks to the fstab file in Lubuntu 14.04 but apparently they don't work well with the new kernel in 15.10-or so the message states that I have duplicate entries in fstab that is apparently preventing booting to Desktop. 

Is there a way to edit the fstab file in Recovery Mode? That way I can just take out all the tweaks.

I have attempted to edit files before in Recovery Mode. Somehow never did accomplish that. I could never even open the files, much less edit them.

Also, thank you to all of you who helped me develop a Bootable Lubuntu Flash Drive. Worked perfectly, that is, until got too tweaky with fstab.

Any assistance you can provide would be much appreciated. That way I don't have to do a complete reinstall, given the error appears to be solely associated with fstab. Well. . .I hope that is the issue.

---

### Post by deadflowr on 2015-12-01
Recovery mode will allow you to open the file, but it runs in read-only mode, so you need to remount it read/write.
Or else any edits done will be lost upon exit/reboot/shutdown.
You should be able to remount by opening the root shell and running:
```
mount -o remount,rw /
```
this should enable it to read/write.
Recovery Mode runs as root, so if there is a problem of actually opening, viewing, or editing, then something else would be amiss.

I wold use nano as the editor (some would suggest vi; dealer's choice)
```
nano /etc/fstab
```
ctrl +o to save then ctrl +x to exit, or ctrl +X to save and exit.
(ctrl +o if you want to keep working on it, ctrl +x if you simply want to save and exit.)

If you want to simply view the file you can use cat or even less.
```
cat /etc/fstab
less /etc/fstab
```

hope it helps

---

### Post by Bucky Ball on 2015-12-01
*Thread moved to **General Help**.*

---

### Post by roler2 on 2015-12-01
Thank you for the instructions. I first had to do some form of disk check which activated the read/write mode and then I added the "mount -o remount,rw /." (without the quotes).


I was then able to utilize nano and edit the fstab file. Still there were errors upon reboot yet eventually booted to Desktop.


Lubuntu 15.10 is working very poorly at the moment. I may have to reinstall with 14.04. I will try a reinstall with 15.10 first.

Thank you again for your assistance.

---

### Post by Bucky Ball on 2015-12-01
If this problem is fixed, or at least resolved, please see the first link in my signature to help others. This will not close the thread for further discussion. :)

---

