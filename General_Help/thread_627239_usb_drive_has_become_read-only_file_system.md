---
title: "usb drive has become read-only file system"
date: 2007-11-29
forum: General Help
---

### Post by tashazo on 2007-11-29
and no matter what I do, I can't seem to get it back to regular.
If I sudo chmod 755 /media/disk/
> 
chmod: changing permissions of `/media/disk/': Read-only file system

If I  sudo chown natasha /media/disk/, I get:
> 
chown: changing ownership of `/media/disk/': Read-only file system
[/QUOTE]

if I do cat /etc/mtab:
> /dev/sda5 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.22-14-386/volatile tmpfs rw 0 0
/dev/sda6 /home ext3 rw,nosuid,nodev 0 0
/dev/sda2 /media/windows fuseblk rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096 0 0
securityfs /sys/kernel/security securityfs rw 0 0
nfsd /proc/fs/nfsd nfsd rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
/dev/sdb1 /media/disk vfat rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077,usefree 0 0

so I can't delete files from the usb drive anymore, whether directly from the drive's trash folder or from my computer's trash folder, whether in nautilus or in the terminal...
it seemed to have started when a certain folder on there was acting funny (I couldn't transfer it to another computer, looked like it had corrupt files...)
pls help! (I'm on gutsy)

---

### Post by -grubby on 2007-11-29
connect your USB drive and go to system>administration>partition editor and delete the partition and recreate it (make sure to backup all data on it) and see if that works

---

### Post by p_quarles on 2007-11-29
It definitely sounds like the drive is corrupted. I agree with nathangrubb's advice here: copy the files onto your hard-disk (since you do have read permissions, right?) and then format the disk.

That said, this might not save the drive itself. You didn't say whether this was a USB flash drive or hard disk, but if it's flash, keep in mind that those have relatively short life cycles compared to other drives. Too many read/writes and they're done for.

---

### Post by jflaker on 2007-11-29
I have the same issue.  My USB HARD DISK is read only........actually, the permissions and OWNER was root, hence, I was not allowed to write or read to the disk.  I believe this was because GPARTED needs to be run SUDO (as it asks for a password)

---

### Post by p_quarles on 2007-11-29
> **jflaker said:**
> I have the same issue.  My USB HARD DISK is read only........actually, the permissions and OWNER was root, hence, I was not allowed to write or read to the disk.  I believe this was because GPARTED needs to be run SUDO (as it asks for a password)
That sounds like a very different issue, actually. If the owner is root, you should be able to run:
```
gksudo nautilus
```
Then, navigate to the external drive, and change the owner to your own user.

---

### Post by tashazo on 2007-11-30
> **p_quarles said:**
> It definitely sounds like the drive is corrupted. I agree with nathangrubb's advice here: copy the files onto your hard-disk (since you do have read permissions, right?) and then format the disk.

That said, this might not save the drive itself. You didn't say whether this was a USB flash drive or hard disk, but if it's flash, keep in mind that those have relatively short life cycles compared to other drives. Too many read/writes and they're done for.


It said it's read only (it was perfectly fine before).  Oh, and it's a flash drive, but really it's my newest one.  I'll be upset if it's fried.  I will try and see if it will let me do what you said and post back.
Thanks.

---

### Post by -grubby on 2007-11-30
> **tashazo said:**
> It said it's read only (it was perfectly fine before).  Oh, and it's a flash drive, but really it's my newest one.  I'll be upset if it's fried.  I will try and see if it will let me do what you said and post back.
Thanks.

while actually flash drives do act kind of like hard drives...they have partitions too

---

### Post by tashazo on 2007-11-30
so I was not able to do anything with my usb flash drive in ubuntu.  i could stick it in, it would automount, but then i could not unmount it, whether from the desktop or nautilus or partition editor (which needs it unmounted so i could format it).
so what I ended up doing was just booting into my windows partition and doing it there - it changed it from fat16 to fat32.  but now it works again.

i don't really know how it got messed up so bad (this is 1 place where windows 'just works' haha) in ubuntu, but thanks guys, for helping me out.
=D>

---

