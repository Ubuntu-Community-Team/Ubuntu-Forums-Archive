---
title: "Problems with DNS"
date: 2007-02-06
forum: General Help
---

### Post by Hauru on 2007-02-06
hi i just installed ubuntu 6.06 and I'm trying System>Administration>Networking to add and edit the DNS server. everything works fine but everytime I reboot, the DNS will revert to the default DNS...ubuntu doesn't seem to be saving the DNS address..

another problem I have is when I'm trying to change the mount points of my partitions in Disk Manager, I clicked ok and the program exits...but when I started Disk Manager again, the mount point is still the old, default moint point. Again, Ubuntu doesn't seem to be saving the changes I've made. 

Need some help here! Any workarounds or solutions for these 2 problems?

THanks!!

---

### Post by christhemonkey on 2007-02-06
For the DNS, if you save (at the top of the dialog box), then it will (should) restore your changes.


For the mount points could you supply us with the output of this command in a terminal:
```
cat /etc/fstab 
```
And then tell us what you would like your preferred monut points to be?

---

### Post by Hauru on 2007-02-06
thanks for the quick reply..

the DNS problem returned to haunt me, this time it just reverts to the default value even without a reboot...what troubles me is that everytime it reverts to the default DNS value, I would have to change the DNS Server address again...

as for the mount point:
<file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda4       /share          vfat    defaults,utf8,umask=007,gid=46 0       1/dev/hda3       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0

i'd like to change the mount point of /share to /media/hda4 ...but i just cant seem to do it in the GUI from Disk Manager... i tried manually editting the fstab file but that wouldn't help as well

---

### Post by Surgeon General on 2007-02-06
hi, are you using DHCP for your ip settings?

---

### Post by Hauru on 2007-02-06
yes I'm using DHCP..

---

### Post by Surgeon General on 2007-02-08
if you're using DHCP it'll always change that. for whatever reason, just edit your dhclient.conf file in /etc/dhcp3 and append this:

prepend domain-name-servers 127.0.0.1;

to the end. of course change the ip address to what DNS server ip you want. separate multiple entries with a space.

hth.

---

