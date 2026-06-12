---
title: "CD Drive frozen shut with drive not recognized, can't eject"
date: 2014-10-25
forum: General Help
---

### Post by NutrOn on 2014-10-25
I ran a movie in wine now it is not recognized in my ubuntu system after a reboot and the physical drive is frozen shut and can't manually eject or force eject with paperclip.

Mount gets me these errors: 

```
mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=userX)
```

In wine sudo eject /dev/sr0 gets me /dev/sr0: block special 
and sudo eject -i off gets me CD-Drive may be ejected with device button
but then but the drive is still locked and the system still does not see a cd drive.
Other note are that I have a netflix compholio install alongside the normal wine install.

---

### Post by Bucky Ball on 2014-10-25
Please use code tags when posting code. See the last link in my signature to find out how. Thanks and good luck.

---

### Post by prshah on 2014-10-25
> **NutrOn said:**
> after a reboot and the physical drive is frozen shut and can't manually eject or force eject with paperclip.

Unfortunately, this seems to be a hardware problem that has nothing to do with NetFlix, WINE or Ubuntu. you can check this by attempting to eject at the BIOS setup screen.

Note that if a WINE program is disallowing eject, then you can use the command ```
wine eject
``` to eject the drive.

However, it is unlikely to help in this case.

---

