---
title: "Freezing on startup (systemd problem?)"
date: 2017-06-27
forum: General Help
---

### Post by petr.nehez on 2017-06-27
I have a laptop Dell Precision 3510 and my Kubuntu 17.04 very often gets frozen on startup.
What I have seen from "jrounalctl -xb" it gets frozen due to timing out on disks.

The first error I can see there is this:
```
systemd[1]: dev-sda1.device: Job dev-sda1.device/start timed out.
```

I tried to play with /etc/fstab and replaced UUID with /dev/sdXX links but this did not help.
This is output I get:

```
&#269;en 27 07:47:51 NEHEZ-Precision-3510 systemd[1]: dev-sda1.device: Job dev-sda1.device/start timed out.&#269;en 27 07:47:51 NEHEZ-Precision-3510 systemd[1]: Timed out waiting for device dev-sda1.device.
-- Subject: Unit dev-sda1.device has failed
-- Defined-By: systemd
-- Support: http://www.ubuntu.com/support
-- 
-- Unit dev-sda1.device has failed.
-- 
-- The result is timeout.
&#269;en 27 07:47:51 NEHEZ-Precision-3510 systemd[1]: Dependency failed for File System Check on /dev/sda1.
-- Subject: Unit systemd-fsck@dev-sda1.service has failed
-- Defined-By: systemd
-- Support: http://www.ubuntu.com/support
-- 
-- Unit systemd-fsck@dev-sda1.service has failed.
-- 
-- The result is dependency.
&#269;en 27 07:47:51 NEHEZ-Precision-3510 systemd[1]: Dependency failed for /boot/efi.
-- Subject: Unit boot-efi.mount has failed
-- Defined-By: systemd
-- Support: http://www.ubuntu.com/support
-- 
-- Unit boot-efi.mount has failed.
-- 
-- The result is dependency.
&#269;en 27 07:47:51 NEHEZ-Precision-3510 systemd[1]: Dependency failed for Local File Systems.
-- Subject: Unit local-fs.target has failed
-- Defined-By: systemd
-- Support: http://www.ubuntu.com/support
-- 
-- Unit local-fs.target has failed.
-- 
-- The result is dependency.
&#269;en 27 07:47:51 NEHEZ-Precision-3510 systemd[1]: local-fs.target: Job local-fs.target/start failed with result 'dependency'.
&#269;en 27 07:47:51 NEHEZ-Precision-3510 systemd[1]: local-fs.target: Triggering OnFailure= dependencies.
&#269;en 27 07:47:51 NEHEZ-Precision-3510 systemd[1]: boot-efi.mount: Job boot-efi.mount/start failed with result 'dependency'.
&#269;en 27 07:47:51 NEHEZ-Precision-3510 systemd[1]: systemd-fsck@dev-sda1.service: Job systemd-fsck@dev-sda1.service/start failed with result 'dependency'.
&#269;en 27 07:47:51 NEHEZ-Precision-3510 systemd[1]: dev-sda1.device: Job dev-sda1.device/start failed with result 'timeout'.
&#269;en 27 07:47:51 NEHEZ-Precision-3510 systemd[1]: dev-sda3.device: Job dev-sda3.device/start timed out.
&#269;en 27 07:47:51 NEHEZ-Precision-3510 systemd[1]: Timed out waiting for device dev-sda3.device.
-- Subject: Unit dev-sda3.device has failed
-- Defined-By: systemd
-- Support: http://www.ubuntu.com/support
-- 
-- Unit dev-sda3.device has failed.
-- 
-- The result is timeout.
&#269;en 27 07:47:51 NEHEZ-Precision-3510 systemd[1]: Dependency failed for /dev/sda3.
```

Any idea how to fix it?

Full journalctl log is in [ATTACH]275781[/ATTACH].

---

### Post by petr.nehez on 2017-06-27
```
# /etc/fstab: static file system information.#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system>                                 <mount point>   <type>  <options>               <dump>  <pass>
# / was on /dev/sda2 during installation
# UUID=2f75b38f-6fa8-473a-b893-e03514a17b1f
/dev/sda2                                       /               ext4    errors=remount-ro       0       1
# /boot/efi was on /dev/sda1 during installation
# UUID=D926-7D91
/dev/sda1                                       /boot/efi       vfat    umask=0077              0       2
# swap was on /dev/sda3 during installation
/dev/sda3                                       none            swap    sw                      0       0

```

---

### Post by petr.nehez on 2017-06-28
I have a laptop Dell Precision 3510 and my Kubuntu 17.04 very often gets frozen on startup.
What I have seen from "jrounalctl -xb" it gets frozen due to timing out on disks.

The first error I can see there is this:
```
systemd[1]: dev-sda1.device: Job dev-sda1.device/start timed out.
```

I tried to play with /etc/fstab and replaced UUID with /dev/sdXX links but this did not help.
This is output I get:

```
&#269;en 27 07:47:51 NEHEZ-Precision-3510 systemd[1]: dev-sda1.device: Job dev-sda1.device/start timed out.&#269;en 27 07:47:51 NEHEZ-Precision-3510 systemd[1]: Timed out waiting for device dev-sda1.device.
-- Subject: Unit dev-sda1.device has failed
-- Defined-By: systemd
-- Support: http://www.ubuntu.com/support
-- 
-- Unit dev-sda1.device has failed.
-- 
-- The result is timeout.
&#269;en 27 07:47:51 NEHEZ-Precision-3510 systemd[1]: Dependency failed for File System Check on /dev/sda1.
-- Subject: Unit systemd-fsck@dev-sda1.service has failed
-- Defined-By: systemd
-- Support: http://www.ubuntu.com/support
-- 
-- Unit systemd-fsck@dev-sda1.service has failed.
-- 
-- The result is dependency.
&#269;en 27 07:47:51 NEHEZ-Precision-3510 systemd[1]: Dependency failed for /boot/efi.
-- Subject: Unit boot-efi.mount has failed
-- Defined-By: systemd
-- Support: http://www.ubuntu.com/support
-- 
-- Unit boot-efi.mount has failed.
-- 
-- The result is dependency.
&#269;en 27 07:47:51 NEHEZ-Precision-3510 systemd[1]: Dependency failed for Local File Systems.
-- Subject: Unit local-fs.target has failed
-- Defined-By: systemd
-- Support: http://www.ubuntu.com/support
-- 
-- Unit local-fs.target has failed.
-- 
-- The result is dependency.
&#269;en 27 07:47:51 NEHEZ-Precision-3510 systemd[1]: local-fs.target: Job local-fs.target/start failed with result 'dependency'.
&#269;en 27 07:47:51 NEHEZ-Precision-3510 systemd[1]: local-fs.target: Triggering OnFailure= dependencies.
&#269;en 27 07:47:51 NEHEZ-Precision-3510 systemd[1]: boot-efi.mount: Job boot-efi.mount/start failed with result 'dependency'.
&#269;en 27 07:47:51 NEHEZ-Precision-3510 systemd[1]: systemd-fsck@dev-sda1.service: Job systemd-fsck@dev-sda1.service/start failed with result 'dependency'.
&#269;en 27 07:47:51 NEHEZ-Precision-3510 systemd[1]: dev-sda1.device: Job dev-sda1.device/start failed with result 'timeout'.
&#269;en 27 07:47:51 NEHEZ-Precision-3510 systemd[1]: dev-sda3.device: Job dev-sda3.device/start timed out.
&#269;en 27 07:47:51 NEHEZ-Precision-3510 systemd[1]: Timed out waiting for device dev-sda3.device.
-- Subject: Unit dev-sda3.device has failed
-- Defined-By: systemd
-- Support: http://www.ubuntu.com/support
-- 
-- Unit dev-sda3.device has failed.
-- 
-- The result is timeout.
&#269;en 27 07:47:51 NEHEZ-Precision-3510 systemd[1]: Dependency failed for /dev/sda3.
```

Any idea how to fix it?

Full journalctl log is in [ATTACH]275781[/ATTACH].

And my **/etc/fstab** file:
```
# /etc/fstab: static file system information.## Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system>                                 <mount point>   <type>  <options>               <dump>  <pass>
# / was on /dev/sda2 during installation
# UUID=2f75b38f-6fa8-473a-b893-e03514a17b1f
/dev/sda2                                       /               ext4    errors=remount-ro       0       1
# /boot/efi was on /dev/sda1 during installation
# UUID=D926-7D91
/dev/sda1                                       /boot/efi       vfat    umask=0077              0       2
# swap was on /dev/sda3 during installation
/dev/sda3                                       none            swap    sw                      0       0

```

[HR][/HR][https://ubuntuforums.org/showthread.php?t=2364736](https://ubuntuforums.org/showthread.php?t=2364736)

---

### Post by #&amp;thj^% on 2017-06-28
Maybe have a look at 
```
sudo blkid
```
to see your new/or changed UUIDS with possible name errors IE: /dev/sda1
Yours dose show this:
```
# / was on /dev/sda2 during installation
# UUID=2f75b38f-6fa8-473a-b893-e03514a17b1f
/dev/sda2                                       /               ext4    errors=remount-ro       0       1
# /boot/efi was on /dev/sda1 during installation
# UUID=D926-7D91
/dev/sda1                                       /boot/efi       vfat    umask=0077              0       2
# swap was on /dev/sda3 during installation
/dev/sda3                                       none            swap    sw                      0       0
```
Just my small effort to help.:)

---

### Post by petr.nehez on 2017-06-29
For those interested in fixing of this issue, see [https://askubuntu.com/questions/929799/](https://askubuntu.com/questions/929799/).

---

### Post by petr.nehez on 2017-06-29
For those interested in fixing of this issue, see [https://askubuntu.com/questions/929799/](https://askubuntu.com/questions/929799/).

---

### Post by QIII on 2017-06-29
Threads merged.

---

