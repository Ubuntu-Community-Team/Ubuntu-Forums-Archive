---
title: "checkfs failed"
date: 2007-04-16
forum: General Help
---

### Post by c_plus_plus on 2007-04-16
I recently found a new problem on my computer where, on boot, my computer would tell me that the fsck failed. It told me it saved a log file to /var/log/fsck/checkfs. I have attached the said file, changing the extension to enable me to upload it. I am able to type control-D and continue the rest of the way /w boot. Could anyone please help me remove the error?

---

### Post by rmemm on 2007-04-17
Here is a thought -- it looks like fsck is trying to fund a storage device that is labeled by a UUID.  It also looks like -- it didn't find it.  Probably you have a device with this UUID defined in your /etc/fstab file.

Have you removed a hard drive, partitian, or other block storage device recently or moved or changed one -- if so that could have caused this?  

You need to figure out if this is a storage device that should be accessable and isn't or if it just shouldn't be there at all.  In the latter case -- you could comment out the line in your fstab.  In the former -- that may mean you just don't boot properly etc -- so be careful with this.

Rob

---

### Post by c_plus_plus on 2007-04-17
The problem is definitely the later! :D  I recently installed a new graphics card and my power supply was not giving power to the whole computer. I decided to unplug some unused drives! Ill go and remove the fstab lines I dont need. Thankyou!

---

