---
title: "Resized partition won't mount"
date: 2007-02-22
forum: General Help
---

### Post by madsporkmurderer on 2007-02-22
I have deleted a few unneeded partitions on a disk and resized the only required one to fill the disk, now this partition refuses to mount.

the device is hda and the remaining partition is hda5, a vfat partition inside hda2, an extended partition. when I attempt to mount hda5 it returns "mount: /dev/hda5 already mounted or /mnt/shared busy"; I have tried different directories, which only changes the directory listed in the error and /dev/hda5 is not listed by mount -a.

I have not backed up the data as it is not unrecoverable, but it would be nice to not have to put it all back to how it was, is there a way to recover it or have I utterly broken it.

Thanks in anticipation

---

### Post by floke on 2007-02-22
you could try 'sudo umount /dev/hda5' and then try to remount it
I had this issue with a partition - was being told it was already mounted multiple times - but once unmounted I could get it back.
To remount: try something like...

mkdir /home/[yourname]/Desktop/hda5
mount /dev/hda5 /home/[yourname]/Desktop/hda5

Hopefully should work

Good luck

---

### Post by madsporkmurderer on 2007-02-22
Thanks for the suggestion, but attempting to umount it results in "umount: /dev/hda5: not mounted"

---

### Post by floke on 2007-02-23
Is it listed in the fstab? And can you see it in your system monitor filesystem?

---

### Post by madsporkmurderer on 2007-02-23
It is not listed in system manager and is in fstab but noauto:

```
/dev/hda5       /mnt/shared     vfat    defaults,utf8,umask=007,gid=46,noauto 0       1
```

---

### Post by floke on 2007-02-24
Ok try this. First create a directory where it will be mounted, something like

mkdir /home/[username]/Desktop/hda5

Then backup the fstab in case this goes wrong

sudo cp /etc/fstab /etc/fstab_backup

Then edit the fstab entry for the partition to this

/dev/hda5 /home/[username]/Desktop/hda5 vfat nodev,nosuid 0 2

This 'should' mount the partition in the directory 'hda5' on your desktop.

---

### Post by madsporkmurderer on 2007-02-26
nope, still getting

```
mount: /dev/hda5 already mounted or /home/mike/Desktop/hda5 busy
```

---

### Post by starling on 2007-03-27
I was getting the very same problem. In the end i fixed it by following the 3g-ntfs howto. That is to say, his suggestion for the fstab line:

/dev/<your partition>     /media/<mount point>     ntfs-3g     defaults,locale=en_US.utf8   0    0

not sure which part of this fixed the problem, and now I don't really care. But if you ask my opinion, I always thought that 'umask' looked a bit shifty ;)

---

