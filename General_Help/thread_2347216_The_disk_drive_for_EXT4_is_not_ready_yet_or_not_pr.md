---
title: "The disk drive for EXT4 is not ready yet or not present."
date: 2016-12-22
forum: General Help
---

### Post by desoto12 on 2016-12-22
On boot, I get the following error message (in red).  I don't know which drive it is.  There are two partitions formatted as ext4 (see below the error message). Can someone enlighten me?  This is a dual boot, Win10 and Ubuntu 14.04.   The OS's are on the SSD (sdb) and i recently moved /home to the HDD (sda).

[COLOR=#ff0000]The disk drive for EXT4 is not ready yet or not present.[/COLOR]
[COLOR=#ff0000]
Continue to wait; or press S to skip mounting or M for manual recovery.[/COLOR]

blkid shows:

/dev/sda1: LABEL="my_data" UUID="23d5929a-084f-4795-9304-95146517b3a3" TYPE="ext4" 
/dev/sda2: LABEL="MY_WINDATA" UUID="63FB-D41E" TYPE="vfat" 
/dev/sdb1: LABEL="ESP" UUID="ACED-3688" TYPE="vfat" 
/dev/sdb3: LABEL="Recovery" UUID="3CCCEDDFCCED9404" TYPE="ntfs" 
/dev/sdb4: LABEL="Acer" UUID="6296F30996F2DD0B" TYPE="ntfs" 
/dev/sdb5: LABEL="ubuntu" UUID="ceae5922-fdbe-4b8b-805e-f5ef9b4824de" TYPE="ext4"

---

### Post by oldos2er on 2016-12-22
Can we see your fstab? ```
cat /etc/fstab
```

---

### Post by desoto12 on 2016-12-23
Thanks for the prompt response!

here is the result of cat /etc/fstab

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb5 during installation
UUID=ceae5922-fdbe-4b8b-805e-f5ef9b4824de /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sdb1 during installation
UUID=ACED-3688  /boot/efi       vfat    defaults        0       1
# swap was on /dev/sdb6 during installation
#UUID=b4f872d1-628a-4bc3-bed5-776f66c432d0 none            swap    sw              0       02
UUID=62ee54c1-7359-4552-be8a-29b9533529ab       ext4          nodev,nosuid       0       2
# (identifier)  (location, eg sda5)   (format, eg ext3 or ext4)      (some settings) 
UUID=23d5929a-084f-4795-9304-95146517b3a3   /home    ext4          defaults       0       2 


Is this UUID=62ee54c1-7359-4552-be8a-29b9533529ab       ext4          nodev,nosuid       0       2  the one causing the error message?

---

### Post by nothingspecial on 2016-12-23
62ee54c1-7359-4552-be8a-29b9533529ab doesn't have a mountpoint

---

### Post by desoto12 on 2016-12-23
Ah, good point, nothingspecial.  I will have to read up on what mountpoint it should be and how to add one.  I'm new enough to this that I can get my system into trouble, but then I learn a lot correcting my errors.  Thanks so much!

---

### Post by oldos2er on 2016-12-23
See [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab) and [https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

If you need further help, please don't hesitate to ask.

---

### Post by desoto12 on 2016-12-24
Thank you for the links, oldos2er.  Good information.  It's a lot to sort out, but i'm going to give it a go.  If I can't figure it out, I will start a new thread with mountpoint topic.
For now, i simply commented out the partition in fstab so it won't try to mount at boot.  It works fine now, without any error message, so accomplished my original goal.
Thank you both for taking the time during the holidays to help me out.
I will marked this SOLVED!

---

