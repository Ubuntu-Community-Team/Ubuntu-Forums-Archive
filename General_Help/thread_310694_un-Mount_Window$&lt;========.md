---
title: "un-Mount Window$&lt;====/===="
date: 2006-12-01
forum: General Help
---

### Post by ZERO_SHIFT on 2006-12-01
I have a dual booting laptop. When start Ubuntu it automticaly mounts the windows partition. 

How can I stop it from doing so as they apear on my desktop after booting?
 
Thanks in Advance.

---

### Post by apjone on 2006-12-01
edit /etc/fstab and just take out the entry that maps your windowz partition

---

### Post by steve.horsley on 2006-12-01
Better still, add the option **noauto** to the option list in /etc/fstab. You might also want to add option **umask=0** to allow read/write access, and option **user** to allow normal users (as well as root) to mount/umount the partition.

---

### Post by dbk927 on 2006-12-01
If you still want it mounted, just not on your desktop, you can also do the following:

In the terminal:

sudo mkdir /mnt/windows
sudo gedit /etc/fstab

Then when fstab opens change the line of your windows partition.  Where it says /media/hda* change it to say /mnt/windows
Then reboot and it'll be off your desktop, but you can still get to it when you need it by going to the folder "mnt" and then "windows"

*this number will vary depending on where the partition is.

---

### Post by SyvanX on 2006-12-01
If you really don't want it mounted for some reason, and dbk's method doesn't work for you.

sudo gedit /etc/fstab

then add ",noauto" (no quotes) to the options section, remove "auto" if it's in the options too.  This way you can quickly mount it if you need to but you don't have to delete the settings.

---

### Post by ZERO_SHIFT on 2006-12-04
Thanks alot for the replies.

---

