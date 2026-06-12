---
title: "Is there a way to specify where removable storage will mount"
date: 2013-04-21
forum: General Help
---

### Post by CaptainMark on 2013-04-21
I have an attached usb hdd which I use for backup's and I want it mounted in a specific place for various reasons, (lets say for arguments sake it has to be mounted at /mnt/passport1) I currently use fstab to mount it which works reasonably well but if the passport1 is not plugged in at boot then the boot sequence hangs telling me it's not there waiting for a response. 
Is there a way to specify where to mount removable storage, the keyword being removable, so if its not there the computer will plod along regardless, but when I plug it in based on it's uuid it will always be mounted to the same location (of my choosing)

---

### Post by rnerwein on 2013-04-21
hi
apend your mount options in /etc/fstab with "noauto". i think if you need it just call: mount /mnt/passport1. i think that will work.
ciao

---

### Post by CaptainMark on 2013-04-22
Will this still mount the drive automatically when the drive is 'hot' plugged in (during use) and if it is present at boot, I should have said, any option I use has to be family friendly, so no ongoing command line work I'm afraid.

EDIT: Why did I ask you to do my leg work for me, it does seem to still mount automatically during use which is good thank you  (i was put off by the term noauto sounding as though this wouldnt mount without command line interaction)

---

