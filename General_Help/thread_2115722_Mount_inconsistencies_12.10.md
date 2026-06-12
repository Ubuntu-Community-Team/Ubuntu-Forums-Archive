---
title: "Mount inconsistencies 12.10"
date: 2013-02-13
forum: General Help
---

### Post by graysky on 2013-02-13
Booting the desktop-amd64 iso in a VM (2 GB of RAM allotted) and select 'try ubuntu' I see that the liveCD environment shows 1 GB of tmpfs mounted to /tmp as I would expect.

If I go on to install to my VM, then reboot, I do not see any tmpfs mounted to /tmp at all... why?

Live environment in the VM:
```
$ mount  | grep tmpfs
udev on /dev type devtmpfs (rw,mode=0755)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)

$ df -h | grep tmpfs
tmpfs           401M  752K  400M   1% /run
tmpfs          1002M   20K 1002M   1% /tmp
```

After installing to the VM's HDD and rebooted without the CD image:
```
% mount  | grep tmpfs
udev on /dev type devtmpfs (rw,mode=0755)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)

% df -h | grep tmpfs
df: `/run/user/lightdm/gvfs': Permission denied
tmpfs           401M  768K  400M   1% /run

```

---

### Post by haqking on 2013-02-13
> **graysky said:**
> Booting the desktop-amd64 iso in a VM (2 GB of RAM allotted) and select 'try ubuntu' I see that the liveCD environment shows 1 GB of tmpfs mounted to /tmp as I would expect.

If I go on to install to my VM, then reboot, I do not see any tmpfs mounted to /tmp at all... why?

Live environment in the VM:
```
$ mount  | grep tmpfs
udev on /dev type devtmpfs (rw,mode=0755)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)

$ df -h | grep tmpfs
tmpfs           401M  752K  400M   1% /run
tmpfs          1002M   20K 1002M   1% /tmp
```After installing to the VM's HDD and rebooted without the CD image:
```
% mount  | grep tmpfs
udev on /dev type devtmpfs (rw,mode=0755)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)

% df -h | grep tmpfs
df: `/run/user/lightdm/gvfs': Permission denied
tmpfs           401M  768K  400M   1% /run

```


Because you have installed to a HDD, a live CD loads to ram (tmpfs)

if you want to use tmpfs then configure it in your fstab, but per your other thread [http://ubuntuforums.org/showthread.php?t=2115743](http://ubuntuforums.org/showthread.php?t=2115743) why would you want tmpfs in a VM out of interest ?

Though perhaps I dont understand your question ?

---

### Post by graysky on 2013-02-13
> **haqking said:**
> Because you have installed to a HDD, a live CD loads to ram (tmpfs)

if you want to use tmpfs then configure it in your fstab, but per your other thread [http://ubuntuforums.org/showthread.php?t=2115743](http://ubuntuforums.org/showthread.php?t=2115743) why would you want tmpfs in a VM out of interest ?

Though perhaps I dont understand your question ?

I installed it to a VM for testing purposes.  I recently ported [profile-sync-daemon](http://ubuntuforums.org/showthread.php?t=2115685) to Ubuntu and I needed a test box.  There is only so much you can do via a chroot :)

---

### Post by haqking on 2013-02-13
> **graysky said:**
> I installed it to a VM for testing purposes.  I recently ported [profile-sync-daemon]("http://ubuntuforums.org/showthread.php?t=2115685") to Ubuntu and I needed a test box.  There is only so much you can do via a chroot :)

Fair enough ;-)

Peace

---

