---
title: "Lost access to my raid drive?"
date: 2013-01-12
forum: General Help
---

### Post by RTIInstaller on 2013-01-12
was working fine, now it wont show up in thunar. it shows up as sdc1 mounted in the disc management utility. I am not sure what is going on with this.
 cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc  nodev,noexec,nosuid  0  0  
# / was on /dev/sda1 during installation
UUID=d80b81b8-3030-46e4-b2e7-b70e802f5281  /            ext4  errors=remount-ro    0  1  
# swap was on /dev/sda5 during installation
UUID=53036505-44bb-4009-b519-bffe4324d5ff  none         swap  sw                   0  0  
/dev/sdb1                                  /media/sdb1  ext2  errors=remount-ro    0  0  
/dev/sdc1                                  /media/sdc1  ext2  defaults             0  0

oh and xbmc can see the raid drive and the movies there on but it wont play them anymore

---

### Post by tgalati4 on 2013-01-12
Check your log files in /var/log.  Post any related messages.

---

