---
title: "USB storage device permissions"
date: 2008-05-04
forum: General Help
---

### Post by Brian2615 on 2008-05-04
Using hardy I automount a USB removable hard disk [NTFS] and there is no trash.
If I mount a USB key [vfat] there *is* a trash.

The difference is related to the volume permissions apparently - changing to user ownership allows a two-stage delete.
Currently the two devices mount as follows:

for the HD
drwxrwxrwx 1 root root 4096 2008-05-02 18:30 disk 

mtab entry
/dev/sdc1 /media/disk fuseblk rw,nosuid,nodev,noatime,allow_other,blksize=4096 0 0


 
for the key
drwx------ 17 bag  root 16384 1970-01-01 10:00 disk

mtab entry
/dev/sdc1 /media/disk vfat rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush 0 0

Does anyone know how & where can I permanently change the config files for the HDD so that it automounts with the user as owner? This is a bit deep for me. A simple "chown" returns 
chown: changing ownership of `disk': Operation not permitted

---

### Post by Brian2615 on 2008-05-22
Well... if I use Thunar, stuff deleted from the ntfs USB hdd appears in my trash folder - permissions haven't changed. 

But in any event, I no longer need the answer to this question :)

---

### Post by vibinlakshman on 2008-05-22
plz google the file /etc/fstab , after that u will knw it ... Appreciate the output friend

---

### Post by Brian2615 on 2008-05-22
fstab doesn't help for automounted USB media - after all I can mount an ntfs HDD and a vfat usb key in the same slot and if there were an fstab entry things would screw up right royally for one or the other!

---

