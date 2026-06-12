---
title: "CDrom drive not appearing"
date: 2007-07-26
forum: General Help
---

### Post by sonic256 on 2007-07-26
Hi,

I'm running xubuntu 6.06.1 LTS right now and working on getting upgraded to 7.06.  Until this evening my cd drive has worked fine, and now its not recognizing disks when I'm loggin in.  I had the 6.10 alt disk in my drive when I booted and the install dialog came up, so I know the drive is working, and the cds are good.  But once I get logged in, I can't find the cd.  cdrom0 appears in /media but no data.  Could someone help me out, Thank You.

---

### Post by dragonwings on 2007-07-27
im having the same thing i found if i clicked on the flopy drive that the cd/dvd drive would show

---

### Post by sonic256 on 2007-07-27
sorry, but that didn't work for me.

---

### Post by anaconda on 2007-07-27
does it work if you mount it manually (from terminal) ?

eg.
sudo mount /dev/cdrom /media/cdrom0

(doing it like this it wont appear on your desktop, but you can access your cd from /cdrom or /media/cdrom0 ..)

---

