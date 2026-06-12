---
title: "updating initramfs?"
date: 2007-12-19
forum: General Help
---

### Post by staceyofthelamp on 2007-12-19
Im runnng 7.10 from vista, everything is fine apart from a sound problem. to debug the sound i need to update my alsa, to do thing i need to use update-initramfs, however the /boot partition is ro.
is there a reason its ro?
is there an easy way to remount rw?
are there problems updating my initramfs?

---

### Post by bernied on 2007-12-19
You can remount with the mount command, try this (in a terminal):
```
sudo mount -o remount,rw /boot
```
Once you've done this the update should work fine.

It will be set to be read only in the /etc/fstab file, which is editable by root only. Not such a bad thing, apart from this inconvenience.

---

### Post by staceyofthelamp on 2007-12-19
nope i still get /boot as read only
i also tried unmounting then remounting, but i only ever get ro

i think its to do with it being on an ntfs partition
i have ntfs-3g installed

edit: got it to work i think
i did a lazy unmount, ln -s to a fake dir then updated that dir, then coped t over which was ok, not sure why update-initramfs was so insistant that it was ro

---

### Post by bernied on 2007-12-19
hmmmm, i'm getting out of my depth as I've never tried to access ntfs filesystems from linux.
Can you normally write to your ntfs partitions?

the output from the following might be helpful:
```
mount
cat /etc/fstab
```

---

### Post by ago on 2007-12-20
sudo update-initramfs -c -k $(uname -r)

---

