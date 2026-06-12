---
title: "UUID fstab Isuue"
date: 2018-02-19
forum: General Help
---

### Post by MotoTom on 2018-02-19
I'm working on a headless server using Ubuntu 16.04.

blkid shows my USB hard drive as "192ebb6c-fa1d-4184-ae7d-68fdefff6ec9"

My fstab looks like this:
```
me@Rock64:~$ cat /etc/fstab
LABEL=boot /boot/efi vfat defaults 0 0
/dev/sda1 /media/MV ext3 auto,nofail,noatime,rw,user 0 0
;UUID=192ebb6c-fa1d-4184-ae7d-68fdefff6ec9 /media/MV ext3 auto,nofail,noatime,rw,user 0 0

```

This works but if I comment out the "/dev/sda1" and enable the UUID line the drive does not mount. I'd really like to specify which drive mounts to /media/MV

Any thought or suggestions will be greatly appreciated.

---

### Post by yetimon_64 on 2018-02-19
For this question the full output of "**sudo blkid -c /dev/null -o list**"  (without the quotes) would be a good idea to post. The switch "-c  /dev/null" ensures the command is not using any cached values and polls  all of your hardware directly. The "-o list" switch is an option to  order the output for easier reading.

By doing this helpers here will be able to see your situation more  clearly. By showing full values that are currently in use we will be  able to see any possible errors you are making which may explain why the UUID entry is failing.

---

