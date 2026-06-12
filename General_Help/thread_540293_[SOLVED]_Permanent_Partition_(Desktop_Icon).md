---
title: "[SOLVED] Permanent Partition (Desktop Icon)"
date: 2007-09-01
forum: General Help
---

### Post by _simon_ on 2007-09-01
Is there anyway I can stop my permanently mounted partition from showing on the desktop?

I still want to have icons for my camera, phone, memory stick etc. when I plug them in though.

---

### Post by forestpixie on 2007-09-01
I don't think you can - my stick doesn't show on the desktop when I plug it in - and I have desktop icons turned off

I think they're all counted as volumes

---

### Post by kayvortex on 2007-09-01
I *think* forestpixie is right. What you can do is put an applet on your panel that shows all mounted fs's: these are out of the way and small enough to not be annoying. The relevent one is "Disk Mounter".

---

### Post by _simon_ on 2007-09-01
Cheers kayvortex, I'll see how I get on with that applet.

---

### Post by vanadium on 2007-09-01
There *is* away to have your permanently mounted volumes not appear as an icon, while preserving icons for removable devices. However, it requires you to mount your permanent drive in a different place than /media.

It is actually quite easy to do.

* In /etc/fstab, look up the line of your permanent volume. The second entry indicates the mount point and will look like  /media/name_of_your_volume. Change that entry to /mnt/name_of_your_volume instead (since you post this under "general help" rather than the beginners forum, I supose you know you must edit as root and create a backup of your fstab before you start)

* Now create the new mount point you specified in /etc/fstab: sudo mkdir /mnt/name_of_your_volume Make sure it has the same permissions as your old moint point, /media/name_of_your_volume

* reload fstab: "sudo mount -a". Now, you should be able to access your volume from /mnt/name_of_your_volume instead of /media/name_of_your_volume. The desktop icon will be gone. You may delete the old mount point.

---

### Post by _simon_ on 2007-09-01
^ that's fantastic mate, worked a treat :)

Just a note for anyone else following that, I had to reboot for the change to take affect.

---

