---
title: "Partition not ready yet Again &gt;:("
date: 2015-03-03
forum: General Help
---

### Post by dallase1 on 2015-03-03
I installed a new 4 TB external SATA Hard Drive and took my old 2 TB External SATA Hard Drive and made it an internal drive and now I'm getting the message at boot up  "Partition not ready yet"I had this happen once before when I had to reinstall windows but I was able to fix it by editing the fstab file but since only 1 parttion had changed it id it was easy to fix. Now that I have 3 partitions that seemed to have changed and the one new one from the external 4 TB drive it is a lot more confusing to figure out how to edit the fstab file. I spent a half an hour or more trying to figure out how to edit the fstab file but it made my head spin looking at it's complexity I'm Not a super advanced user and don't understand any advanced commands or options in Linux. Why is there not some program that can analyze the fstab file and compare it to the actual ids of all the partitions?

where is the log file that contains any messages you see at boot up like the drive not ready or not present error?


I checked the file boot.log and this is what was in it

I faile to see how this makes Linux better then Windows, at least when you add new hardware or new partitions Windows can still boot without any errors or if it does get errors it can usually fix them by it's self other then if you add a new partition before the Windows Partition after installing Windows.
ata_id[454]: HDIO_GET_IDENTITY failed for '/dev/sdd': Invalid argument 
  
ata_id[459]: HDIO_GET_IDENTITY failed for '/dev/sde': Invalid argument 
  
fsck from util-linux 2.20.1 
udevd[652]: specified group 'adbusers' unknown 
  
ata_id[878]: HDIO_GET_IDENTITY failed for '/dev/sdd': Invalid argument 
  
ata_id[929]: HDIO_GET_IDENTITY failed for '/dev/sde': Invalid argument 
  
/dev/sda5: clean, 1479195/6316032 files, 16647049/25250816 blocks 
NTFS signature is missing. 
Failed to mount '/dev/sdd1': Invalid argument 
The device '/dev/sdd1' doesn't seem to have a valid NTFS. 
Maybe the wrong device is used? Or the whole disk instead of a 
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around? 
mountall: mount /media/System Reserved [1278] terminated with status 12 
mountall: Filesystem could not be mounted: /media/System Reserved 
Mount is denied because the NTFS volume is already exclusively opened. 
The volume may be already mounted, or another software may use it which 
could be identified for example by the help of the 'fuser' command. 
mountall: mount /media/System_Reserved_ [1288] terminated with status 16 
mountall: Filesystem could not be mounted: /media/System_Reserved_ 
Skipping /media/System Reserved at user request 
Skipping /media/System_Reserved_ at user request 
Skipping LABEL="TOSHIBA at user request 
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox 
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox-trunk 
Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd 
 * Starting AppArmor profiles       [160G  [154G[ OK ] 
 * Setting sensors limits       [160G  [154G[ OK ] 
Starting VMware services: 
   Virtual machine monitor[71G done 
   Virtual machine communication interface[71G done 
   VM communication interface socket family[71G done 
   Blocking file system[71G done 
   Virtual ethernet * Starting LightDM Display Manager[154G[ OK ] 
 * Stopping Send an event to indicate plymouth is up[154G[ OK ] 
 * Stopping save kernel messages[154G[ OK ]


where is the log file that contains any messages you see at boot up like the drive not ready or not present error?

---

### Post by oldfred on 2015-03-03
Best to post these:

sudo parted -l
       sudo blkid -c /dev/null -o list
cat /etc/fstab

You do not normally mount by device like sdd or sde but by UUID, so if drive number changes from one to another it does not matter. And if mounting by device and sdd1 was ext4 but now the new sdd1 is NTFS it creates all sorts of issues.

 Understanding fstab
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://wiki.archlinux.org/index.php/Fstab](https://wiki.archlinux.org/index.php/Fstab)

log files are in /var/log/dmesg, you should be able to review with log file view or just any editor.

---

