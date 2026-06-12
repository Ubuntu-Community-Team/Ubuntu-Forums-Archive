---
title: "Have to setup RAID every boot"
date: 2013-05-11
forum: General Help
---

### Post by jaw2floor on 2013-05-11
Hi there,

I have 2x500gb hard drives in (Windows) software raid0, and have been able to access the array by using the following commands:

```
sudo mdadm --build /dev/md0 --chunk=64 --level=0 --raid-devices=2 /dev/sda1 /dev/sdb1
```
```
sudo mount -t ntfs /dev/md0 /media/Windows
```

Upon restarting my computer, the array is no longer accessible, until I enter these commands again.

Is there a way to run these commands automatically at startup, or am I using the wrong commands?

Thanks,
Liam

---

### Post by SaturnusDJ on 2013-05-11
That's because you use build mode. [http://linux.die.net/man/8/mdadm](http://linux.die.net/man/8/mdadm)
Because no metadata is saved, the array can't start automatically...unless ofcourse you script the commands you post.

What you want is to use the create mode. **Warning:** I don't know if data will be intact if you just use create mode over a build array.

After using create mode, the output of "mdadm --detail --scan" needs to go in /etc/mdadm/mdadm.conf. Then run "update-initramfs -u". Then add mount options to /etc/fstab.

---

### Post by jaw2floor on 2013-05-11
Ahh right.

Could you lead me in the right direction on how I can get the commands to run on startup? I don't want to try create mode

Thanks

---

### Post by SaturnusDJ on 2013-05-12
I don't know the best place to put it, so you can add the entry to /etc/fstab...but if you just paste your two lines of code before 'exit 0' in /etc/rc.local, it will happen on boot.

---

