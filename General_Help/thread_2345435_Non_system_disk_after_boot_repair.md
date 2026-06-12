---
title: "Non system disk after boot repair"
date: 2016-12-04
forum: General Help
---

### Post by veecee on 2016-12-04
After using boot repair to try and fix a boot problem I have getting into Lubuntu (after a normal, clean switch off). I was previously able to see
 the Grub menu, but none of the options worked. Now, I get the error message stating that I have a non-system disk. Getting back on using the boot repair disk, I can see that there is a problem regarding mounting the disk volume: error message is:

 Error mounting /dev/sda1 at
 /media/lubuntu/1dbb8489-a78f-4094-b93e-da4c808fe04e: Command-line `mount -t
 "ext4" -o "uhelper=udisks2,nodev,nosuid" "/dev/sda1"
 "/media/lubuntu/1dbb8489-a78f-4094-b93e-da4c808fe04e"' exited with non-zero
 exit status 32: mount: wrong fs type, bad option, bad superblock on
 /dev/sda1,
        missing codepage or helper program, or other error
        In some cases useful info is found in syslog - try dmesg | tail  or so
 
 The link to the Boot repair data is [Http://paste.ubuntu.com/23577076](Http://paste.ubuntu.com/23577076)

Thank you for any assistance with this. Please keep responses in noobie mode :)

Vernon

---

### Post by yancek on 2016-12-04
I would try running a filesystem check with the fsck command on sda1 and see what the results are.

What was the 'boot problem' you had before running boot repair?  Boot repair doesn't report very much because the partition can't be mounted therefore the information is not accessible.

---

