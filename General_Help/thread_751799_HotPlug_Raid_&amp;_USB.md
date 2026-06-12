---
title: "HotPlug Raid &amp; USB"
date: 2008-04-10
forum: General Help
---

### Post by justinshafer on 2008-04-10
What do you guys think of this? Linux just aint there yet. I have a server with a raid array and two partitions. A data paritions, and a boot parition with applications on it as well.

The data partitions is mirrored to a third device, a usb device, which I am trying to add to the raid array around 9:30 am and then its removed when the doctor disconnects it. We have 5 of them.

After awhile raid doesnt seem to fully work, and MD1 the data array is filled with /dev/sdf2 g2 h2 and on down the list it goes...

I could reboot it daily to see if that helps... Any ideas?

My crontab. Sdparm fixed a problem but its still not fully reliable. I am actually using grm linux which is based on debian and has hardware support with every boot. 

The idea is this. If the server for some reason wont work, then the usb drive can be hooked up to another pc, told to boot from it, and it will then boot grml off the usb drive, and use the data directory on the drive to make samba and mysql work. I would have used ubuntu but I cant recall why I didnt. I think its because it doesnt have automatic hardware detection on every boot. Probably just going to convert to ubuntu and acronis tomorrow. Cheers!

*/5 * * * * /sbin/mdadm --manage --add /dev/md1 /dev/disk/by-id/usb-Seagate_FreeAgent_Go_5LY48F4B-0:0-part2
15 9 * * * /sbin/mdadm --manage --fail /dev/md1 /dev/disk/by-id/usb-Seagate_FreeAgent_Go_5LY48F4B-0:0-part2
20 9 * * * /sbin/mdadm --manage --remove /dev/md1 /dev/disk/by-id/usb-Seagate_FreeAgent_Go_5LY48F4B-0:0-part2
35 9 * * * /sbin/sdparm --clear STANDBY -6 /dev/disk/by-id/usb-Seagate_FreeAgent_Go_5LY48F4B-0:0-part2
*/4 * * * * /sbin/mdadm --manage --add /dev/md1 /dev/disk/by-id/usb-Seagate_FreeAgent_Go_5LY3XA72-0:0-part2
15 9 * * * /sbin/mdadm --manage --fail /dev/md1 /dev/disk/by-id/usb-Seagate_FreeAgent_Go_5LY3XA72-0:0-part2
20 9 * * * /sbin/mdadm --manage --remove /dev/md1 /dev/disk/by-id/usb-Seagate_FreeAgent_Go_5LY3XA72-0:0-part2
35 9 * * * /sbin/sdparm --clear STANDBY -6 /dev/disk/by-id/usb-Seagate_FreeAgent_Go_5LY3XA72-0:0-part2
*/3 * * * * /sbin/mdadm --manage --add /dev/md1 /dev/disk/by-id/usb-Seagate_FreeAgent_Go_5LY1X2J7-0:0-part2
15 9 * * * /sbin/mdadm --manage --fail /dev/md1 /dev/disk/by-id/usb-Seagate_FreeAgent_Go_5LY1X2J7-0:0-part2
20 9 * * * /sbin/mdadm --manage --remove /dev/md1 /dev/disk/by-id/usb-Seagate_FreeAgent_Go_5LY1X2J7-0:0-part2
35 9 * * * /sbin/sdparm --clear STANDBY -6 /dev/disk/by-id/usb-Seagate_FreeAgent_Go_5LY1X2J7-0:0-part2
*/2 * * * * /sbin/mdadm --manage --add /dev/md1 /dev/disk/by-id/usb-Seagate_FreeAgent_Go_5LY3VSME-0:0-part2
15 9 * * * /sbin/mdadm --manage --fail /dev/md1 /dev/disk/by-id/usb-Seagate_FreeAgent_Go_5LY3VSME-0:0-part2
20 9 * * * /sbin/mdadm --manage --remove /dev/md1 /dev/disk/by-id/usb-Seagate_FreeAgent_Go_5LY3VSME-0:0-part2
35 9 * * * /sbin/sdparm --clear STANDBY -6 /dev/disk/by-id/usb-Seagate_FreeAgent_Go_5LY3VSME-0:0-part2

---

