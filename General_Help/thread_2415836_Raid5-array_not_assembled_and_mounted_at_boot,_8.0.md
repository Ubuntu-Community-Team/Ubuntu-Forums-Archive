---
title: "Raid5-array not assembled and mounted at boot, 8.04"
date: 2019-04-01
forum: General Help
---

### Post by MagnusL on 2019-04-01
Hi!

I have a brand new installation of Ubuntu 18.04, where I was planning on having a raid5-array of 3 harddrives. 

I've installed mdadm and followed the instructions here: 

[https://www.digitalocean.com/community/tutorials/how-to-create-raid-arrays-with-mdadm-on-ubuntu-18-04](https://www.digitalocean.com/community/tutorials/how-to-create-raid-arrays-with-mdadm-on-ubuntu-18-04)

My problem is that the volume is not assembled nor mounted at boot - I need to reassemble it for every boot. Data is there, though. So what might be wrong or missing?

My mdadm.conf: 

```
# mdadm.conf
#
# !NB! Run update-initramfs -u after updating this file.
# !NB! This will ensure that initramfs has an uptodate copy.
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default (built-in), scan all partitions (/proc/partitions) and all
# containers for MD superblocks. alternatively, specify devices to scan, using
# wildcards if desired.
#DEVICE partitions containers

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR magnus@vista.se

# definitions of existing MD arrays

# This configuration was auto-generated on Mon, 25 Mar 2019 20:49:25 +0100 by mkconf
# ARRAY /dev/md0 metadata=1.2 name=vista7:0 UUID=6d20fdd7:0573e9a0:e0f98827:21f9f386
ARRAY /dev/md0 metadata=1.2 spares=1 name=vista7:0 UUID=b0fafa8f:75bb659b:46dc7fd8:0a98161a

```

My fstab: 

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=519f7548-b1ef-4d24-8976-29d953096af0 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
#UUID=0C8A-0ADA  /boot/efi       vfat    umask=0077      0       1
# /home was on /dev/sda4 during installation
UUID=50c68cb0-7766-48db-aee4-598d41cb6e13 /home           ext4    defaults        0       2
# swap was on /dev/sda3 during installation
UUID=3ea4d33e-7b88-492c-8e54-35245eab84ef none            swap    sw              0       0
/dev/sde1	/home/magnus/astro_1GB	ext4	defaults	0	0
UUID=0C8A-0ADA	/boot/efi	vfat	defaults	0	1
# /dev/md0 /mnt/md0 ext4 defaults,nofail,discard 0 0
/dev/md0 /home/magnus/astro_raid ext4 defaults,nofail,discard 0 0

```

I did run $ sudo update-initramfs -u

I find no error msgs or similar, nothing linked to mdadm, when running dmesg after boot. SO what am I missing here?

Magnus

---

### Post by mörgæs on 2019-04-01
Is it Ubuntu 8.04 or 18.04?

---

### Post by MagnusL on 2019-04-01
Hi!
Of course, 18.04. Is 8.04 even possible to run, 10 years too late?

---

### Post by mörgæs on 2019-04-02
I am often surprised to see how much old stuff people still install.
Good that it's recent. If you change the thread title you will prevent confusion.

---

### Post by MagnusL on 2019-04-02
Hi!

I cannot see how I can change the thread title. Any suggestions? And any suggestions on my problem?

Magnus

---

