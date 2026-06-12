---
title: "UBUNTU 13.10 will not load"
date: 2014-03-19
forum: General Help
---

### Post by nineball69 on 2014-03-19
Out of nowhere ubuntu 13.10 will not boot up. I was getting the initramfs prompt. I have loaded the live CD, and it is from there that I am typing my question. This is a dual boot and I am able to access my files in windows 7 from the live CD. When I click on the ubuntu section I get this error message

Unable to access “29 GB Volume”

Error mounting /dev/sda5 at /media/ubuntu/2de451af-5339-484a-b88b-1b0ba4133164: Command-line `mount -t "ext4" -o "uhelper=udisks2,nodev,nosuid" "/dev/sda5" "/media/ubuntu/2de451af-5339-484a-b88b-1b0ba4133164"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/sda5,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

can someone guide me on how to mount this drive. I have alot of important files.

Thanks

---

### Post by bookrt on 2014-03-20
Sounds like it could be a corrupted sector. I would recommend trying to boot with a USB Ubuntu disk and see if you can access the HDD. Depending on what you find, you can back up your important data, then decide whether to reinstall or attempt to repair.

---

### Post by nineball69 on 2014-03-20
Thanks for the reply.

Any more suggestions, this must have happened to others.

---

### Post by bookrt on 2014-03-23
what is your fstab entry for /dev/sda5? It is possible there is something wrong there...but the fact that this happened out of nowhere tells me that it is a hardware issue. Can you boot to Windows and run SMART testing on this drive?

---

### Post by nineball69 on 2014-03-23
> **bookrt said:**
> what is your fstab entry for /dev/sda5? It is possible there is something wrong there...but the fact that this happened out of nowhere tells me that it is a hardware issue. Can you boot to Windows and run SMART testing on this drive?

How would I go about finding the fstab entry?  What would it show me? My only concern is to retrieve the data.

---

### Post by Impavidus on 2014-03-24
The fstab is in the file /etc/fstab, which you can't reach as you're unable to mount the partition. You can check your drive's smart status from the live disk. To me this sounds as file system damage or a hardware failure. I don't have experience with it, but have a look here: [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery). Make backups next time.

---

### Post by bookrt on 2014-03-24
/etc/fstab is the file that tells Ubuntu which partitions to mount (and the correct order) as it is booting up. The error you are getting is indicating that the partition that fstab is pointing to is not there. You could boot to Ubuntu using a rescue disk and then look into this file to make sure it is correct. If you have not changed fstab, that means something has changed with the hardware--either it has been disconnected or corrupted. If some sectors are corrupted, it is possible to repair or reinstall the HDD. 

Regardless, I believe your first order of business is to create a Ubuntu rescue disk on a USB stick and use it to boot into a working Ubuntu system that you can then use to retrieve the data and fix the problem.

---

### Post by Impavidus on 2014-03-24
OP already booted from a live disk and couldn't mount the root partition. See post #1. There is file system damage. Nothing wrong with /etc/fstab, as that wouldn't affect the live session.

---

### Post by bookrt on 2014-03-24
Oops, I had forgotten about that. In that case, yes, carry on as lmpavidus recommends. You might start with filesystem check (fsck) of the partition in question:

fsck /dev/sda5

If that does not work, then try testdisk per the tutorial recommended by lmpavidus.

---

