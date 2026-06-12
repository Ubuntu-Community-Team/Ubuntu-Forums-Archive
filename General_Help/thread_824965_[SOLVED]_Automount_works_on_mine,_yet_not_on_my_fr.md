---
title: "[SOLVED] Automount works on mine, yet not on my friends?"
date: 2008-06-10
forum: General Help
---

### Post by Psyphre on 2008-06-10
Hi, a friend of mine installed gutsy and unfortunately his ntfs partitions will not mount. I managed to solve the problem on mine by editing fstab, yet doing the same on his doesnt work at all. Obviously i altered the uuid numbers to match his partitions, so that isnt the issue.

Please does anyone have any idea wat is causing this? He's new to linux and has had nothing but troubles so far, would be a shame if he ended up going back to xp so soon.

Heres his fstab if that helps:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=1a4a46e2-ca23-4fae-89f8-bb59ea87992b /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=863002F83002EECD /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=515E4872F5C94D64 /media/sda5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb2
UUID=CECCCBA5CCCB8665 /media/sdb2     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb5
UUID=E218033918030C6B /media/sdb5     ntfs    defaults,umask=007,gid=46 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0


Thanks in advance :)

---

### Post by logos34 on 2008-06-10
did you create the mountpoints in /media?  What if any error messages do you get at startup?

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
[https://help.ubuntu.com/community/MountingWindowsPartitions?highlight=%28windows%29#head-c067eb7e3cd4107cc08cdf30a9e1aed8adb02971](https://help.ubuntu.com/community/MountingWindowsPartitions?highlight=%28windows%29#head-c067eb7e3cd4107cc08cdf30a9e1aed8adb02971)

---

### Post by drs305 on 2008-06-10
> **Psyphre said:**
> Hi, a friend of mine installed gutsy and unfortunately his ntfs partitions will not mount. I managed to solve the problem on mine by editing fstab, yet doing the same on his doesnt work at all. Obviously i altered the uuid numbers to match his partitions, so that isnt the issue.

Please does anyone have any idea wat is causing this? He's new to linux and has had nothing but troubles so far, would be a shame if he ended up going back to xp so soon.


# /dev/sda5
UUID=515E4872F5C94D64 /media/sda5     ntfs    defaults,umask=007,gid=46 0       1


Thanks in advance :)

We don't have a lot to go on here, but has he created the mount point (/media/sda5) on his computer?

Second, does he have **ntfs-config** installed on his computer? ntfs-config shows NTFS partitions that can be mounted and allows you to select which ones are. The app will make the appropriate changes to your system.

---

### Post by Psyphre on 2008-06-10
thanks for the replies.

logos34: i did not ask him to create the mount points, since i asked him to check the folder /media and the mount points were already there. Didnt get any errors on start up, the partitions simply do not show up anywhere (except in the /media folder).

drs305: yup the mount points are there. havent got ntfs-config, i will ask him to try it and then let u know.

---

### Post by Psyphre on 2008-06-11
Found out the reason, he didnt shut down windows properly, all of this was all due to that one reason lol. It all works now. Thanks alot for the help though.

---

