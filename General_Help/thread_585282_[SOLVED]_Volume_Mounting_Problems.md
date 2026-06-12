---
title: "[SOLVED] Volume Mounting Problems"
date: 2007-10-21
forum: General Help
---

### Post by MadhavS on 2007-10-21
I am running a hard drive that is partitioned into three parts, one with XP, one with the Gutsy 32 bit, and one with the Gutsy 64 bit. From my 64 bit gutsy, i can read and write to either of the other two OS's. From my 32 bit, i can read and write to windows, but cannot even see my 64-bit's stuff. When I went to home folder, i tryed to mount it (it showed a 30 GB volume on the left hand bar, and i right clicked on it and pressed mount), but got this error: 

 Cannot mount volume.

Unable to mount the volume. Details: mount_point cannot contain the following characters: newline, G_DIR_SEPARATOR (usually /)

I'm not really sure what to do at this point in order to view the volume. Can someone give me advice on what this error means and what to do?

Thanks in advance.

---

### Post by pondochris on 2007-10-21
I'm guessing you installed in order: windows>32 bit>64 bit. In that case you may need to make an entry for it in /etc/fstab file. You will also need to make a directory to mount it in. Mine are all in /media. The 64 bit if it was installed after would have done this automatically during the install process. When I installed debian after buntu and windows I could not mount the debian partition at first because there was no entry in fstab or a mount point for it and when I tried to mount it wanted to mount in / because that is where it mounted when I booted that partition. Hope this helps.

---

### Post by MadhavS on 2007-10-21
What kind of entry should i make in /etc/fstab?

Im looking at the other entries, like for my 32-bit partition itself, on /dev/sda2, and it says:

UUID=e037d194-2195-4ecb-b0b0-7503159b8dfa /               ext3    defaults,errors=remount-ro 0       1

What should i put for my 64-bit, which is /dev/sda3?

Thanks for any help.

---

### Post by MadhavS on 2007-10-22
Ok, i managed to get it to work by making a new directory in /media and mounting the volume into that by adding lines to my /etc/mtab and /etc/fstab. Thank you for the help pondochris!

---

