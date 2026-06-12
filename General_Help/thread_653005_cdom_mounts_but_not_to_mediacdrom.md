---
title: "cdom mounts but not to /media/cdrom"
date: 2007-12-29
forum: General Help
---

### Post by jasorn on 2007-12-29
In gutsy cdroms mount but not to /media/cdrom.  Rather they mount to /media/volume where volume is the name of the cd.  How do I make them mount to /media/cdrom?

---

### Post by taurus on 2007-12-29
See if you can unmount it first and then mount it to wherever you want.

```
sudo umount /media/volume
sudo mkdir /media/cdrom
sudo mount -t iso9660 /dev/sdc1 /media/cdrom
df -h
```
_Assuming_ your CDROM is /dev/sdc1.

---

### Post by jasorn on 2007-12-29
Thanks for the reply.  I can mount it manually just fine.  The question is why does the automount thing not mount to /media/cdrom like it used to?  And how to I make it do that.  Just about all my apps that have cdrom support expect it to mount to /media/cdrom.  I don't want to have to manually mount them.

---

### Post by taurus on 2007-12-29
Maybe you need to have a look in /etc/fstab to see what is the entry for your CDROM look like.

```
cat /etc/fstab
```

---

### Post by jasorn on 2007-12-29
There are the cdrom lines in fstab.  

/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdd /media/cdrom1 udf,iso9660 user,noauto 0 0

But has this changed?  I've used ubuntu for years now and haven't had this behavior.

---

### Post by ~LoKe on 2007-12-29
My guess is hdd and hdc are no longer the names of your cd drives.

---

### Post by jasorn on 2007-12-29
No, those are the names.  This is a new install.  I just wiped the fstab and rebooted and it's working the way I expect.

Thanks for the super quick replies.

I'll chalk this up to gremlins.

---

### Post by jasorn on 2007-12-29
No, those are the names.  This is a new install.  I just wiped the fstab and rebooted and it's working the way I expect.

Thanks for the super quick replies.

I'll chalk this up to gremlins.

---

### Post by taurus on 2007-12-29
Look at dmesg to be sure.

```
dmesg | more
```
Hit the space bar for the next 24 lines.

---

