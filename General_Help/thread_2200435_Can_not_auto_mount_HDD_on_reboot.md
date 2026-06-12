---
title: "Can not auto mount HDD on reboot"
date: 2014-01-19
forum: General Help
---

### Post by mike127 on 2014-01-19
Can not auto mount hard drives on reboot


mdadm --examine --scan
```
ARRAY /dev/md/1 metadata=1.2 UUID=b8acb790:132cb703:740bc037:6f76ecdd name=xbmc-System-Product-Name:1
ARRAY /dev/md/0 metadata=1.2 UUID=c9142c5e:d46dd380:880371ff:1cc49962 name=xbmc-System-Product-Name:0



```


mdadm.conf
```
# mdadm.conf#
# Please refer to mdadm.conf(5) for information about this file.
#


DEVICE partitions


# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes


# automatically tag new arrays as belonging to the local system
HOMEHOST <system>


# instruct the monitoring daemon where to send mail alerts
MAILADDR root


# definitions of existing MD arraysARRAY /dev/md/xbmc-System-Product-Name:0 metadata=1.2 name=xbmc-System-Product-Name:0 UUID=c9142c5e:d46dd380:880371ff:1cc49962
ARRAY /dev/md/xbmc-System-Product-Name:1 metadata=1.2 name=xbmc-System-Product-Name:1 UUID=b8acb790:132cb703:740bc037:6f76ecdd



```


my fstab
```
# /etc/fstab: static file system information.#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=83c759ee-cd43-491d-bd2d-774d4a9cbc17 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=c4fd54a0-05c3-4584-a4cf-8054e70622bc none            swap    sw              0       0


UUID=c9142c5e:d46dd380:880371ff:1cc49962 /home/media     ext4    defaults         0      2
UUID=b8acb790:132cb703:740bc037:6f76ecdd /home/backups     ext4    defaults         0      2



```





I get this everytime
[IMG]http://i.imgur.com/17Fv7Op.jpg[/IMG]


Any ideas? because I'm out of them.

---

### Post by TheFu on 2014-01-19
My UUIDs have '-', not ':' characters.

Check with either 
```
ls -al /dev/disk/by-uuid/
```
or 
```
blkid
```
commands.

---

