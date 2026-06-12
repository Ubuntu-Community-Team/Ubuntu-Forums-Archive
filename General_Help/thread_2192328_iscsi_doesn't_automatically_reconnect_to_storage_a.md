---
title: "iscsi doesn't automatically reconnect to storage after reboot"
date: 2013-12-07
forum: General Help
---

### Post by tornado_moore_03 on 2013-12-07
We are running 12.04.3 LTS and are having issues with trying to get our iscsi target to reconnect after server is rebooted. The node.startup = automatic is configured in iscsid.conf. We do not use CHAP for authenticating the connection. 
We have this listed in /etc/fstab
/dev/sdc1       /storage        ext4    defaults,auto,_netdev   0       0

[EMAIL="root@server1:~$"]root@server1:~$[/EMAIL] sudo iscsiadm -m node --targetname "iqn.2001-05.com.equallogic:0-8a0906-aa74e2a08-8480019fb2152a24-server2" --portal "10.128.115.100:3260" --login
Logging in to [iface: eth0, target: iqn.2001-05.com.equallogic:0-8a0906-aa74e2a08-8480019fb2152a24-server2, portal: 10.128.115.100,3260]
Login to [iface: eth0, target: iqn.2001-05.com.equallogic:0-8a0906-aa74e2a08-8480019fb2152a24-server2, portal: 10.128.115.100,3260]: successful
[EMAIL="root@server1:~$"]root@server1:~$[/EMAIL]
[EMAIL="denadmin@server1:~$"]denadmin@server1:~$[/EMAIL] sudo iscsiadm -m session
tcp: [1] 10.128.115.100:3260,1 iqn.2001-05.com.equallogic:0-8a0906-aa74e2a08-8480019fb2152a24-server2

[EMAIL="root@server1:~$"]root@server1:~$[/EMAIL] mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /var/lib/lightdm/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=lightdm)
/dev/sdc1 on /storage type ext4 (rw,_netdev)

[EMAIL="root@server1:~$"]root@server1:~$[/EMAIL] sudo fdisk -l
Disk /dev/sda: 49.4 GB, 49392123904 bytes
255 heads, 63 sectors/track, 6004 cylinders, total 96468992 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000705df
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    71329791    35663872   83  Linux
/dev/sda2        71331838    96466943    12567553    5  Extended
/dev/sda5        71331840    96466943    12567552   82  Linux swap / Solaris
Disk /dev/sdb: 218.2 GB, 218238025728 bytes
255 heads, 63 sectors/track, 26532 cylinders, total 426246144 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00041bf6
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   401104895   200551424   83  Linux
/dev/sdb2       401106942   426244095    12568577    5  Extended
/dev/sdb5       401106944   426244095    12568576   82  Linux swap / Solaris
Disk /dev/sdc: 1099.5 GB, 1099526307840 bytes
118 heads, 9 sectors/track, 2022139 cylinders, total 2147512320 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000f2bf4
   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048  2147512319  1073755136   83  Linux



Any help is greatly appreciated. Thx

---

### Post by ace6 on 2014-09-15
I had a similar problem in which I managed to solve. 

What happened in my case is that every time the server reboots it would bring up the iscsi with a different Disk, one time it was /dev/sdd the next it would be /dev/sdb etc

What I did to solve it was use the UUID instead of the Disk (Header) or whatever you call it instead. To do this, issue the following commands on your server

cd /dev/disk/by-uuid
ls -l 

or ls -l /dev/disk/by-uuid

This will give you the UUID's for all the Disks that are available. Copy the UUID that your iscsi is currently using, if you're not sure use this

fdisk -l | grep Disk

it will show you the Disks. You should be able to tell your iscsi by its size. 

Edit the fstab with : vi /etc/fstab 
and add 
UUID=[iscsi UUID] /mountdir ext4 noatime,defaults 0 2

That should solve the connection on reboot issue

But can you also check your Host-to-VirutalDrive Mapping on your SAN Management, I also had a problem where the iscsi connected fine during reboot but couldn't execute the mount from fstab cause the VirtualDrive in the SAN wasn't mapped correctly or wasn't mapped at all. 

Let me know how that goes if you haven't solved this already.

---

### Post by ace6 on 2014-09-15
Sorry if that doesn't make sense, I'm a Beginner to Ubuntu. :)

---

