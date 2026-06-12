---
title: "Trying to mount Truecrypt drive without it opening in Nautilus"
date: 2014-07-30
forum: General Help
---

### Post by echo59 on 2014-07-30
Hi,
lum
I just upgraded to Trusty from Precise.  I'd it set up that after I log in, my Truecrypt volume would be auto-mounted.  But I had it that the volume wouldn't open with a Nautilus window.

Anyway, since my upgrade this has gone awry.  Now when I log in, I'm prompted for my Truecrypt password, then once the volume is mounted a Nautilus window opens.

The output from *sudo blkid* is as follows:
> /dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D9-0210" TYPE="vfat" 
/dev/sda2: LABEL="RECOVERY" UUID="1450971850970022" TYPE="ntfs" 
/dev/sda3: LABEL="OS" UUID="4EA89A78A89A5DF1" TYPE="ntfs" 
/dev/sda5: UUID="30edba92-104a-458e-aed7-b871e44eb4b3" TYPE="ext4" 
/dev/sda6: UUID="7dd78db5-c44e-4d5e-a319-977eaf1a92f9" TYPE="swap" 
/dev/mapper/truecrypt1: LABEL="DATAPART1" UUID="2E86A08E86A0585B" TYPE="ntfs" 

My */etc/fstab* file is as follows:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>


proc    /proc    proc    defaults    0    0
#Entry for /dev/sda5 :
UUID=30edba92-104a-458e-aed7-b871e44eb4b3    /    ext4    errors=remount-ro    0    1
#Entry for /dev/sdb1 :
#UUID=2E86A08E86A0585B    /media/DATAPART1    ntfs-3g    defaults,locale=en_IE.UTF-8    0    0
#(Hash out after Truecrypt)
#Entry for /dev/sda3 :
UUID=4EA89A78A89A5DF1    /media/OS    ntfs-3g    defaults,nosuid,nodev,locale=en_IE.utf8    0    0
#Entry for /dev/sda6 :
UUID=7dd78db5-c44e-4d5e-a319-977eaf1a92f9    none    swap    sw    0    0


For the life of me, I can't figure out how I corrected the problem the last time.  I'd appreciate any help that people can give with this.  It is probably something silly that I'm forgetting.....

---

### Post by echo59 on 2015-04-04
Easy solution = change settings in dconf-editor
[http://askubuntu.com/questions/191527/disable-auto-opening-nautilus-window-after-auto-mount](http://askubuntu.com/questions/191527/disable-auto-opening-nautilus-window-after-auto-mount)

Quickly, install *dconf-tools *package and  run dconf-editor.
org > gnome > desktop > media-handling > automount-open deselect

---

