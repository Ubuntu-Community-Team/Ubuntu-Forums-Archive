---
title: "External hard drive mount point moves unintentionally"
date: 2013-10-09
forum: General Help
---

### Post by dberg on 2013-10-09
I am running 13.04 and using an external hard drive as a backup location. When I plug the drive in, it mounts to [COLOR="#0000CD"]/media/My Passport[/COLOR]. However, randomly the mount point changes to [COLOR="#0000CD"]/media/My Passport1[/COLOR] without unplugging the drive (just sitting there idle). The original mount point [COLOR="#0000CD"](/media/My Passport[/COLOR]) is converted to a folder.

I have Crashplan setup to backup to [COLOR="#0000CD"]/media/My Passport/backups[/COLOR]. When the mount point for the external HD changes, Crashplan begins backing to the folder that is left behind which fills up my local hard drive.

How can I keep the mount point for the external HD from changing to prevent this from happening. I would like the mount point to be stable.

---

### Post by whitesmith on 2013-10-09
Probably your best bet is to modify /etc/fstab to boot using UUIDs, not designations such as sda, sda3, etc. Instructions for doing this are all over the forum. Cheers!

---

### Post by dberg on 2013-10-09
So once something is mounted as specified in the fstab file, it is persistent? Can't randomly change later? Also, is the fstab configuration processed each time I connect the drive and not only at startup?

---

### Post by bab1 on 2013-10-09
> **dberg said:**
> So once something is mounted as specified in the fstab file, it is persistent? Can't randomly change later? Also, is the fstab configuration processed each time I connect the drive and not only at startup?

Not necessarily persistent, but it is consistent.  If you add the entry to fstab you can't automagically mount your external drive by just inserting the cable into the USB port.  The fstab file is only read at boot time by the mount command and the entries are mounted as defined.  The only other time the fstab file is read is when you issue the command *mount -a * from the CLI.

I have a feeling your problem is really the drive un-mounting and then immediately trying to remount itself.  That's why the mount point changes.    Why did you create a mount point anyway.  The USB mount will create it's own mount point as you have seen.  What errors do you see in the logs (syslog, dmesg, kern, etc)?

Using fstab should not have any effect upon this failure.

---

### Post by dberg on 2013-10-09
I didn't create any mount point. The one I mentioned is the default created when the drive is plugged in. I will check the error logs when I have a chance and report back.

---

### Post by dberg on 2013-10-09
Here are the log entries that I get after plugging the HD in. I don't necessarily see anything important here but maybe someone else will. It hasn't remounted itself to a different mount point yet so I can't post any log entries directly related to that.


```
Oct  9 21:04:46 Devin-HP kernel: [137647.840927] usb 2-1.1: new high-speed USB device number 7 using ehci-pci
Oct  9 21:04:46 Devin-HP kernel: [137647.934878] usb 2-1.1: New USB device found, idVendor=1058, idProduct=0740
Oct  9 21:04:46 Devin-HP kernel: [137647.934888] usb 2-1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=5
Oct  9 21:04:46 Devin-HP kernel: [137647.934893] usb 2-1.1: Product: My Passport 0740
Oct  9 21:04:46 Devin-HP kernel: [137647.934898] usb 2-1.1: Manufacturer: Western Digital
Oct  9 21:04:46 Devin-HP kernel: [137647.934903] usb 2-1.1: SerialNumber: [REDACTED]
Oct  9 21:04:46 Devin-HP kernel: [137647.935844] scsi6 : usb-storage 2-1.1:1.0
Oct  9 21:04:46 Devin-HP mtp-probe: checking bus 2, device 7: "/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1"
Oct  9 21:04:46 Devin-HP mtp-probe: bus: 2, device: 7 was not an MTP device
Oct  9 21:04:47 Devin-HP kernel: [137648.933555] scsi 6:0:0:0: Direct-Access     WD       My Passport 0740 1003 PQ: 0 ANSI: 6
Oct  9 21:04:47 Devin-HP kernel: [137648.934156] scsi 6:0:0:1: Enclosure         WD       SES Device       1003 PQ: 0 ANSI: 6
Oct  9 21:04:47 Devin-HP kernel: [137648.935708] sd 6:0:0:0: Attached scsi generic sg2 type 0
Oct  9 21:04:47 Devin-HP kernel: [137648.935908] ses 6:0:0:1: Attached Enclosure device
Oct  9 21:04:47 Devin-HP kernel: [137648.936076] ses 6:0:0:1: Attached scsi generic sg3 type 13
Oct  9 21:04:52 Devin-HP dbus[1049]: [system] Activating service name='org.freedesktop.hostname1' (using servicehelper)
Oct  9 21:04:52 Devin-HP dbus[1049]: [system] Successfully activated service 'org.freedesktop.hostname1'
Oct  9 21:04:52 Devin-HP kernel: [137654.485499] sd 6:0:0:0: [sdb] 1953458176 512-byte logical blocks: (1.00 TB/931 GiB)
Oct  9 21:04:52 Devin-HP kernel: [137654.487463] sd 6:0:0:0: [sdb] Write Protect is off
Oct  9 21:04:52 Devin-HP kernel: [137654.487468] sd 6:0:0:0: [sdb] Mode Sense: 47 00 10 08
Oct  9 21:04:52 Devin-HP kernel: [137654.488824] sd 6:0:0:0: [sdb] No Caching mode page present
Oct  9 21:04:52 Devin-HP kernel: [137654.488830] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Oct  9 21:04:52 Devin-HP kernel: [137654.494486] sd 6:0:0:0: [sdb] No Caching mode page present
Oct  9 21:04:52 Devin-HP kernel: [137654.494497] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Oct  9 21:04:52 Devin-HP kernel: [137654.506610]  sdb: sdb1
Oct  9 21:04:52 Devin-HP kernel: [137654.509899] sd 6:0:0:0: [sdb] No Caching mode page present
Oct  9 21:04:52 Devin-HP kernel: [137654.509910] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Oct  9 21:04:52 Devin-HP kernel: [137654.509922] sd 6:0:0:0: [sdb] Attached SCSI disk
Oct  9 21:04:52 Devin-HP ata_id[20216]: HDIO_GET_IDENTITY failed for '/dev/sdb': Invalid argument
Oct  9 21:04:55 Devin-HP ntfs-3g[20236]: Version 2013.1.13 external FUSE 29
Oct  9 21:04:55 Devin-HP ntfs-3g[20236]: Mounted /dev/sdb1 (Read-Write, label "My Passport", NTFS 3.1)
Oct  9 21:04:55 Devin-HP ntfs-3g[20236]: Cmdline options: rw,nosuid,nodev,uhelper=udisks2,uid=1000,gid=1000,dmask=0077,fmask=0177
Oct  9 21:04:55 Devin-HP ntfs-3g[20236]: Mount options: rw,nosuid,nodev,uhelper=udisks2,allow_other,nonempty,relatime,default_permissions,fsname=/dev/sdb1,blkdev,blksize=4096
Oct  9 21:04:55 Devin-HP ntfs-3g[20236]: Global ownership and permissions enforced, configuration type 7
Oct  9 21:04:55 Devin-HP udisksd[2401]: Removing stale entry for mount point `/media/devin/My Passport' in /run/udisks2/mounted-fs file
Oct  9 21:04:56 Devin-HP udisksd[2401]: Mounted /dev/sdb1 at /media/devin/My Passport on behalf of uid 1000
```

---

### Post by bab1 on 2013-10-10
> **dberg said:**
> I didn't create any mount point. The one I mentioned is the default created when the drive is plugged in. I will check the error logs when I have a chance and report back.

This makes me feel that the problem will reveal itself through the logs.  When the the partition is unmounted in an orderly way (via a command from you), the mount point is destroyed as part of the command.   A random event seems to be causing the disconnect and it is leaving the mount point in place.

We shall just have to wait.

---

### Post by dberg on 2013-10-13
After some more searching around, I think that I may be running into a [known]("https://crashplan.zendesk.com/entries/42691-ubuntu-crashplan-engine-creates-mount-directory-before-actual-mount-external-drive") [issue]("http://ubuntuforums.org/showthread.php?t=1930002") with the Crashplan backup software. I am trying to work out how to get around this issue and figure out how to prevent Crashplan from trying to back up to my external drive if it is not connected/mounted.

---

### Post by bab1 on 2013-10-14
> **dberg said:**
> After some more searching around, I think that I may be running into a [known]("https://crashplan.zendesk.com/entries/42691-ubuntu-crashplan-engine-creates-mount-directory-before-actual-mount-external-drive") [issue]("http://ubuntuforums.org/showthread.php?t=1930002") with the Crashplan backup software. I am trying to work out how to get around this issue and figure out how to prevent Crashplan from trying to back up to my external drive if it is not connected/mounted.

Two things you should consider.  First, don't disable the mount at login function of the external drive.  This is a valid method.  The use has to be given ownership of the drive when it is mounted.  This is why it is not mounted automagically until you login.  

Second, If you want the drive mounted at boot then you have to add the information to the fstab file.  This will cause the auto-mount  function to be internally disabled.  With this you will create the mount point and add to fstab all the other options needed to mount the drive correctly/

I have idea how you are launching CrashPlan.  I've never used the application.  I do launch some applications via a wrapper script so I can set (or check) the environment.  You certainly can check to see if the drive is mounted correctly before allowing CrashPlan to launch.

---

### Post by dberg on 2013-10-14
Crashplan starts up at boot (prior) to login which I think is where most of the issues arise from. Although delaying it until login won't help if I don't have the drive plugged in. The only plausible solution I see was posted at the first link and involved editing the Crashplan init script to check for the drive. Though I'd rather Crashplan could be started to allow for online backup even without drive present.

> I have a similar problem.  I have a lap top and travel a lot without my external drive. So if I reboot without the destination drive present, the local disk fills up unless I remember to stop it.  I added this to /etc/init.d/crashplan which will prevent it from running if the drive is not mounted:

start)
       EXTERNAL_DRIVE=/media/WD\ Ext\ Drive  #Substitute your mount point here
       PARTITION=`df | grep -e "$EXTERNAL_DRIVE$" | cut -f1 -d" "`
       if [ ${#PARTITION} -gt 0 ]; then 
          $SCRIPTNAME start
       else
         echo "$0 not started. $EXTERNAL_DRIVE is not mounted." >&2
       fi    
    ;;

---

### Post by dberg on 2013-10-17
I have been communicating with Crashplan's support. The support person was able to recreate the issue but only if when the drive was unmounted, the mount point folder doesn't get deleted and becomes a filesystem folder. 

This seems like the likely situation of what it happening. For some reason the drive disconnects at random and the mount point folder doesn't get deleted. Crashplan still sees the same destination folder and thus backs up to it.

I still need to try to catch this happening so that I can try to find any log entries related to it.

---

### Post by dberg on 2013-11-01
It finally happened again. I have pasted my syslog but I don't necessarily see anything that looks to contain the fact that the folder was not deleted at any time so I'm not sure that the event was captured in the logs this time either.

```
Oct 31 07:40:42 Devin-HP anacron[17570]: Job `cron.daily' terminated
Oct 31 07:40:42 Devin-HP anacron[17570]: Normal exit (1 job run)
Oct 31 07:50:12 Devin-HP whoopsie[1382]: online
Oct 31 07:51:41  whoopsie[1382]: last message repeated 2 times
Oct 31 08:17:01 Devin-HP CRON[18359]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 31 08:35:12 Devin-HP NetworkManager[1071]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted
Oct 31 08:50:12 Devin-HP whoopsie[1382]: online
Oct 31 08:51:14  whoopsie[1382]: last message repeated 2 times
Oct 31 09:17:01 Devin-HP CRON[18438]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 31 09:20:43 Devin-HP whoopsie[1382]: online
Oct 31 09:22:13 Devin-HP whoopsie[1382]: online
Oct 31 09:23:14  whoopsie[1382]: last message repeated 4 times
Oct 31 09:39:15 Devin-HP whoopsie[1382]: online
Oct 31 09:40:16  whoopsie[1382]: last message repeated 2 times
Oct 31 09:50:12 Devin-HP whoopsie[1382]: online
Oct 31 09:51:17  whoopsie[1382]: last message repeated 2 times
Oct 31 10:17:01 Devin-HP CRON[18529]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 31 10:24:07 Devin-HP whoopsie[1382]: online
Oct 31 10:25:18  whoopsie[1382]: last message repeated 5 times
Oct 31 10:26:18  whoopsie[1382]: last message repeated 2 times
Oct 31 10:27:18  whoopsie[1382]: last message repeated 2 times
Oct 31 10:28:18  whoopsie[1382]: last message repeated 2 times
Oct 31 10:31:16 Devin-HP whoopsie[1382]: online
Oct 31 10:32:17  whoopsie[1382]: last message repeated 2 times
Oct 31 10:33:18  whoopsie[1382]: last message repeated 3 times
Oct 31 10:36:40 Devin-HP whoopsie[1382]: online
Oct 31 10:37:49  whoopsie[1382]: last message repeated 2 times
Oct 31 10:38:23 Devin-HP whoopsie[1382]: online
Oct 31 10:40:22 Devin-HP whoopsie[1382]: online
Oct 31 10:40:23 Devin-HP whoopsie[1382]: online
Oct 31 10:44:10 Devin-HP whoopsie[1382]: online
Oct 31 10:45:11  whoopsie[1382]: last message repeated 2 times
Oct 31 10:46:19  whoopsie[1382]: last message repeated 2 times
Oct 31 10:47:29 Devin-HP whoopsie[1382]: online
Oct 31 10:48:49  whoopsie[1382]: last message repeated 3 times
Oct 31 10:50:12 Devin-HP whoopsie[1382]: online
Oct 31 10:51:19  whoopsie[1382]: last message repeated 2 times
Oct 31 10:52:37 Devin-HP whoopsie[1382]: online
Oct 31 10:54:37 Devin-HP whoopsie[1382]: online
Oct 31 10:54:38 Devin-HP whoopsie[1382]: online
Oct 31 10:56:45 Devin-HP whoopsie[1382]: online
Oct 31 10:57:50  whoopsie[1382]: last message repeated 2 times
Oct 31 10:59:44 Devin-HP whoopsie[1382]: online
Oct 31 11:01:44 Devin-HP whoopsie[1382]: online
Oct 31 11:01:45 Devin-HP whoopsie[1382]: online
Oct 31 11:04:11 Devin-HP whoopsie[1382]: online
Oct 31 11:05:20  whoopsie[1382]: last message repeated 2 times
Oct 31 11:06:48 Devin-HP whoopsie[1382]: online
Oct 31 11:07:50  whoopsie[1382]: last message repeated 3 times
Oct 31 11:08:50  whoopsie[1382]: last message repeated 2 times
Oct 31 11:13:58 Devin-HP whoopsie[1382]: online
Oct 31 11:15:58 Devin-HP whoopsie[1382]: online
Oct 31 11:17:01  whoopsie[1382]: last message repeated 2 times
Oct 31 11:17:01 Devin-HP CRON[18639]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 31 11:17:50 Devin-HP whoopsie[1382]: online
Oct 31 11:17:51 Devin-HP whoopsie[1382]: online
Oct 31 11:21:05 Devin-HP whoopsie[1382]: online
Oct 31 11:23:05 Devin-HP whoopsie[1382]: online
Oct 31 11:24:11  whoopsie[1382]: last message repeated 2 times
Oct 31 11:25:21  whoopsie[1382]: last message repeated 2 times
Oct 31 11:26:53 Devin-HP whoopsie[1382]: online
Oct 31 11:28:12  whoopsie[1382]: last message repeated 3 times
Oct 31 11:30:12 Devin-HP whoopsie[1382]: online
Oct 31 11:30:13 Devin-HP whoopsie[1382]: online
Oct 31 11:35:19 Devin-HP whoopsie[1382]: online
Oct 31 11:36:55 Devin-HP whoopsie[1382]: online
Oct 31 11:38:21  whoopsie[1382]: last message repeated 4 times
Oct 31 11:42:26 Devin-HP whoopsie[1382]: online
Oct 31 11:44:11 Devin-HP whoopsie[1382]: online
Oct 31 11:45:22  whoopsie[1382]: last message repeated 4 times
Oct 31 11:46:58 Devin-HP whoopsie[1382]: online
Oct 31 11:48:22  whoopsie[1382]: last message repeated 2 times
Oct 31 11:49:33 Devin-HP whoopsie[1382]: online
Oct 31 11:50:12 Devin-HP whoopsie[1382]: online
Oct 31 11:51:22  whoopsie[1382]: last message repeated 2 times
Oct 31 11:52:22  whoopsie[1382]: last message repeated 2 times
Oct 31 11:56:41 Devin-HP whoopsie[1382]: online
Oct 31 11:57:43  whoopsie[1382]: last message repeated 4 times
Oct 31 11:58:52  whoopsie[1382]: last message repeated 4 times
Oct 31 12:02:41 Devin-HP whoopsie[1382]: online
Oct 31 12:03:42  whoopsie[1382]: last message repeated 2 times
Oct 31 12:04:47  whoopsie[1382]: last message repeated 3 times
Oct 31 12:05:48  whoopsie[1382]: last message repeated 3 times
Oct 31 12:06:40 Devin-HP whoopsie[1382]: online
Oct 31 12:08:39 Devin-HP whoopsie[1382]: online
Oct 31 12:08:40 Devin-HP whoopsie[1382]: online
Oct 31 12:10:55 Devin-HP whoopsie[1382]: online
Oct 31 12:12:54 Devin-HP whoopsie[1382]: online
Oct 31 12:12:55 Devin-HP whoopsie[1382]: online
Oct 31 12:17:01 Devin-HP CRON[18752]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 31 12:17:06 Devin-HP whoopsie[1382]: online
Oct 31 12:18:02 Devin-HP whoopsie[1382]: online
Oct 31 12:19:24  whoopsie[1382]: last message repeated 2 times
Oct 31 12:20:24  whoopsie[1382]: last message repeated 2 times
Oct 31 12:24:11 Devin-HP whoopsie[1382]: online
Oct 31 12:25:24  whoopsie[1382]: last message repeated 3 times
Oct 31 12:26:24  whoopsie[1382]: last message repeated 3 times
Oct 31 12:27:24  whoopsie[1382]: last message repeated 3 times
Oct 31 12:28:40 Devin-HP whoopsie[1382]: online
Oct 31 12:28:41 Devin-HP whoopsie[1382]: online
Oct 31 12:32:16 Devin-HP whoopsie[1382]: online
Oct 31 12:34:15 Devin-HP whoopsie[1382]: online
Oct 31 12:34:16 Devin-HP whoopsie[1382]: online
Oct 31 12:37:11 Devin-HP whoopsie[1382]: online
Oct 31 12:38:40 Devin-HP whoopsie[1382]: online
Oct 31 12:39:54  whoopsie[1382]: last message repeated 2 times
Oct 31 12:41:22 Devin-HP whoopsie[1382]: online
Oct 31 12:41:23 Devin-HP whoopsie[1382]: online
Oct 31 12:44:11 Devin-HP whoopsie[1382]: online
Oct 31 12:45:12  whoopsie[1382]: last message repeated 2 times
Oct 31 12:46:30 Devin-HP whoopsie[1382]: online
Oct 31 12:47:13 Devin-HP whoopsie[1382]: online
Oct 31 12:48:29 Devin-HP whoopsie[1382]: online
Oct 31 12:49:55  whoopsie[1382]: last message repeated 3 times
Oct 31 12:50:55  whoopsie[1382]: last message repeated 3 times
Oct 31 12:53:37 Devin-HP whoopsie[1382]: online
Oct 31 12:55:36 Devin-HP whoopsie[1382]: online
Oct 31 12:55:37 Devin-HP whoopsie[1382]: online
Oct 31 12:57:16 Devin-HP whoopsie[1382]: online
Oct 31 12:58:45 Devin-HP whoopsie[1382]: online
Oct 31 12:58:46 Devin-HP whoopsie[1382]: online
Oct 31 13:00:44 Devin-HP whoopsie[1382]: online
Oct 31 13:02:43 Devin-HP whoopsie[1382]: online
Oct 31 13:02:44 Devin-HP whoopsie[1382]: online
Oct 31 13:04:11 Devin-HP whoopsie[1382]: online
Oct 31 13:05:12  whoopsie[1382]: last message repeated 2 times
Oct 31 13:07:19 Devin-HP whoopsie[1382]: online
Oct 31 13:07:51 Devin-HP whoopsie[1382]: online
Oct 31 13:08:49 Devin-HP whoopsie[1382]: online
Oct 31 13:09:54  whoopsie[1382]: last message repeated 2 times
Oct 31 13:09:54 Devin-HP whoopsie[1382]: online
Oct 31 13:14:58 Devin-HP whoopsie[1382]: online
Oct 31 13:16:57 Devin-HP whoopsie[1382]: online
Oct 31 13:16:58 Devin-HP whoopsie[1382]: online
Oct 31 13:17:01 Devin-HP CRON[18869]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 31 13:17:21 Devin-HP whoopsie[1382]: online
Oct 31 13:18:51 Devin-HP whoopsie[1382]: online
Oct 31 13:18:52 Devin-HP whoopsie[1382]: online
Oct 31 13:22:05 Devin-HP whoopsie[1382]: online
Oct 31 13:24:04 Devin-HP whoopsie[1382]: online
Oct 31 13:25:11  whoopsie[1382]: last message repeated 3 times
Oct 31 13:25:12 Devin-HP whoopsie[1382]: online
Oct 31 13:27:24 Devin-HP whoopsie[1382]: online
Oct 31 13:28:53 Devin-HP whoopsie[1382]: online
Oct 31 13:29:57  whoopsie[1382]: last message repeated 2 times
Oct 31 13:31:11 Devin-HP whoopsie[1382]: online
Oct 31 13:31:12 Devin-HP whoopsie[1382]: online
Oct 31 13:35:12 Devin-HP NetworkManager[1071]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted
Oct 31 13:36:19 Devin-HP whoopsie[1382]: online
Oct 31 13:37:27 Devin-HP whoopsie[1382]: online
Oct 31 13:38:27  whoopsie[1382]: last message repeated 3 times
Oct 31 13:39:27  whoopsie[1382]: last message repeated 2 times
Oct 31 13:41:58 Devin-HP whoopsie[1382]: online
Oct 31 13:43:26 Devin-HP whoopsie[1382]: online
Oct 31 13:44:27  whoopsie[1382]: last message repeated 5 times
Oct 31 13:45:28  whoopsie[1382]: last message repeated 4 times
Oct 31 13:45:28 Devin-HP whoopsie[1382]: online
Oct 31 13:47:29 Devin-HP whoopsie[1382]: online
Oct 31 13:48:59 Devin-HP whoopsie[1382]: online
Oct 31 13:50:04  whoopsie[1382]: last message repeated 3 times
Oct 31 13:51:28  whoopsie[1382]: last message repeated 5 times
Oct 31 13:52:28  whoopsie[1382]: last message repeated 2 times
Oct 31 13:54:08 Devin-HP whoopsie[1382]: online
Oct 31 13:55:28  whoopsie[1382]: last message repeated 2 times
Oct 31 13:57:32 Devin-HP whoopsie[1382]: online
Oct 31 13:58:58  whoopsie[1382]: last message repeated 2 times
Oct 31 13:59:58  whoopsie[1382]: last message repeated 4 times
Oct 31 14:04:12 Devin-HP whoopsie[1382]: online
Oct 31 14:05:29  whoopsie[1382]: last message repeated 3 times
Oct 31 14:06:41 Devin-HP whoopsie[1382]: online
Oct 31 14:07:58  whoopsie[1382]: last message repeated 3 times
Oct 31 14:09:04 Devin-HP whoopsie[1382]: online
Oct 31 14:10:29  whoopsie[1382]: last message repeated 3 times
Oct 31 14:11:54 Devin-HP whoopsie[1382]: online
Oct 31 14:13:53 Devin-HP whoopsie[1382]: online
Oct 31 14:13:54 Devin-HP whoopsie[1382]: online
Oct 31 14:17:01 Devin-HP CRON[18988]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 31 14:17:37 Devin-HP whoopsie[1382]: online
Oct 31 14:17:43 Devin-HP whoopsie[1382]: online
Oct 31 14:19:01 Devin-HP whoopsie[1382]: online
Oct 31 14:20:29  whoopsie[1382]: last message repeated 2 times
Oct 31 14:21:29  whoopsie[1382]: last message repeated 2 times
Oct 31 14:24:12 Devin-HP whoopsie[1382]: online
Oct 31 14:25:29  whoopsie[1382]: last message repeated 2 times
Oct 31 14:26:08 Devin-HP whoopsie[1382]: online
Oct 31 14:27:28 Devin-HP whoopsie[1382]: online
Oct 31 14:28:30  whoopsie[1382]: last message repeated 3 times
Oct 31 14:29:30  whoopsie[1382]: last message repeated 4 times
Oct 31 14:31:35 Devin-HP whoopsie[1382]: online
Oct 31 14:33:00  whoopsie[1382]: last message repeated 2 times
Oct 31 14:33:15 Devin-HP whoopsie[1382]: online
Oct 31 14:35:14 Devin-HP whoopsie[1382]: online
Oct 31 14:35:15 Devin-HP whoopsie[1382]: online
Oct 31 14:37:13 Devin-HP whoopsie[1382]: online
Oct 31 14:37:42 Devin-HP whoopsie[1382]: online
Oct 31 14:38:43 Devin-HP whoopsie[1382]: online
Oct 31 14:40:00  whoopsie[1382]: last message repeated 3 times
Oct 31 14:40:22 Devin-HP whoopsie[1382]: online
Oct 31 14:42:08 Devin-HP whoopsie[1382]: online
Oct 31 14:43:30  whoopsie[1382]: last message repeated 4 times
Oct 31 14:44:12 Devin-HP whoopsie[1382]: online
Oct 31 14:45:30  whoopsie[1382]: last message repeated 2 times
Oct 31 14:47:29 Devin-HP whoopsie[1382]: online
Oct 31 14:47:45 Devin-HP whoopsie[1382]: online
Oct 31 14:49:28 Devin-HP whoopsie[1382]: online
Oct 31 14:50:31  whoopsie[1382]: last message repeated 2 times
Oct 31 14:51:31  whoopsie[1382]: last message repeated 2 times
Oct 31 14:54:36 Devin-HP whoopsie[1382]: online
Oct 31 14:56:36 Devin-HP whoopsie[1382]: online
Oct 31 14:57:47  whoopsie[1382]: last message repeated 2 times
Oct 31 14:59:17 Devin-HP whoopsie[1382]: online
Oct 31 14:59:18 Devin-HP whoopsie[1382]: online
Oct 31 15:01:43 Devin-HP whoopsie[1382]: online
Oct 31 15:03:43 Devin-HP whoopsie[1382]: online
Oct 31 15:05:01  whoopsie[1382]: last message repeated 2 times
Oct 31 15:06:01  whoopsie[1382]: last message repeated 2 times
Oct 31 15:07:50 Devin-HP whoopsie[1382]: online
Oct 31 15:08:50 Devin-HP whoopsie[1382]: online
Oct 31 15:10:02  whoopsie[1382]: last message repeated 2 times
Oct 31 15:11:02  whoopsie[1382]: last message repeated 2 times
Oct 31 15:14:31 Devin-HP whoopsie[1382]: online
Oct 31 15:15:32  whoopsie[1382]: last message repeated 2 times
Oct 31 15:15:58 Devin-HP whoopsie[1382]: online
Oct 31 15:17:01 Devin-HP CRON[19109]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 31 15:17:52 Devin-HP whoopsie[1382]: online
Oct 31 15:19:02  whoopsie[1382]: last message repeated 2 times
Oct 31 15:20:02  whoopsie[1382]: last message repeated 2 times
Oct 31 15:23:05 Devin-HP whoopsie[1382]: online
Oct 31 15:24:12 Devin-HP whoopsie[1382]: online
Oct 31 15:25:32  whoopsie[1382]: last message repeated 2 times
Oct 31 15:27:55 Devin-HP whoopsie[1382]: online
Oct 31 15:29:24 Devin-HP whoopsie[1382]: online
Oct 31 15:30:32  whoopsie[1382]: last message repeated 2 times
Oct 31 15:32:11 Devin-HP whoopsie[1382]: online
Oct 31 15:32:12 Devin-HP whoopsie[1382]: online
Oct 31 15:37:19 Devin-HP whoopsie[1382]: online
Oct 31 15:37:58 Devin-HP whoopsie[1382]: online
Oct 31 15:39:03  whoopsie[1382]: last message repeated 3 times
Oct 31 15:40:03  whoopsie[1382]: last message repeated 4 times
Oct 31 15:43:12 Devin-HP NetworkManager[1071]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted
Oct 31 15:44:12 Devin-HP whoopsie[1382]: online
Oct 31 15:45:13  whoopsie[1382]: last message repeated 3 times
Oct 31 15:46:33  whoopsie[1382]: last message repeated 2 times
Oct 31 15:48:00 Devin-HP whoopsie[1382]: online
Oct 31 15:49:29 Devin-HP whoopsie[1382]: online
Oct 31 15:50:33  whoopsie[1382]: last message repeated 2 times
Oct 31 15:51:33  whoopsie[1382]: last message repeated 3 times
Oct 31 15:52:48 Devin-HP whoopsie[1382]: online
Oct 31 15:54:02  whoopsie[1382]: last message repeated 4 times
Oct 31 15:55:31 Devin-HP whoopsie[1382]: online
Oct 31 15:55:32 Devin-HP whoopsie[1382]: online
Oct 31 15:58:03 Devin-HP whoopsie[1382]: online
Oct 31 15:58:40 Devin-HP whoopsie[1382]: online
Oct 31 16:00:04  whoopsie[1382]: last message repeated 2 times
Oct 31 16:01:04  whoopsie[1382]: last message repeated 2 times
Oct 31 16:04:12 Devin-HP whoopsie[1382]: online
Oct 31 16:05:13  whoopsie[1382]: last message repeated 2 times
Oct 31 16:05:47 Devin-HP whoopsie[1382]: online
Oct 31 16:07:46 Devin-HP whoopsie[1382]: online
Oct 31 16:09:04  whoopsie[1382]: last message repeated 2 times
Oct 31 16:10:04  whoopsie[1382]: last message repeated 2 times
Oct 31 16:11:04  whoopsie[1382]: last message repeated 2 times
Oct 31 16:12:04  whoopsie[1382]: last message repeated 4 times
Oct 31 16:12:54 Devin-HP whoopsie[1382]: online
Oct 31 16:14:53 Devin-HP whoopsie[1382]: online
Oct 31 16:14:54 Devin-HP whoopsie[1382]: online
Oct 31 16:17:01 Devin-HP CRON[19229]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 31 16:18:08 Devin-HP whoopsie[1382]: online
Oct 31 16:19:37 Devin-HP whoopsie[1382]: online
Oct 31 16:21:05  whoopsie[1382]: last message repeated 2 times
Oct 31 16:22:05  whoopsie[1382]: last message repeated 2 times
Oct 31 16:24:13 Devin-HP whoopsie[1382]: online
Oct 31 16:25:35  whoopsie[1382]: last message repeated 3 times
Oct 31 16:26:35  whoopsie[1382]: last message repeated 2 times
Oct 31 16:27:35  whoopsie[1382]: last message repeated 4 times
Oct 31 16:28:10 Devin-HP whoopsie[1382]: online
Oct 31 16:29:35  whoopsie[1382]: last message repeated 2 times
Oct 31 16:30:35  whoopsie[1382]: last message repeated 5 times
Oct 31 16:31:57 Devin-HP whoopsie[1382]: online
Oct 31 16:33:05  whoopsie[1382]: last message repeated 2 times
Oct 31 16:34:15 Devin-HP whoopsie[1382]: online
Oct 31 16:36:14 Devin-HP whoopsie[1382]: online
Oct 31 16:36:15 Devin-HP whoopsie[1382]: online
Oct 31 16:38:13 Devin-HP whoopsie[1382]: online
Oct 31 16:39:42 Devin-HP whoopsie[1382]: online
Oct 31 16:39:43 Devin-HP whoopsie[1382]: online
Oct 31 16:41:14 Devin-HP whoopsie[1382]: online
Oct 31 16:41:22 Devin-HP whoopsie[1382]: online
Oct 31 16:42:43 Devin-HP whoopsie[1382]: online
Oct 31 16:44:06  whoopsie[1382]: last message repeated 3 times
Oct 31 16:44:13 Devin-HP whoopsie[1382]: online
Oct 31 16:45:36  whoopsie[1382]: last message repeated 2 times
Oct 31 16:48:16 Devin-HP whoopsie[1382]: online
Oct 31 16:48:29 Devin-HP whoopsie[1382]: online
Oct 31 16:49:45 Devin-HP whoopsie[1382]: online
Oct 31 16:50:46  whoopsie[1382]: last message repeated 6 times
Oct 31 16:50:58 Devin-HP whoopsie[1382]: online
Oct 31 16:52:27 Devin-HP whoopsie[1382]: online
Oct 31 16:53:36  whoopsie[1382]: last message repeated 2 times
Oct 31 16:54:37 Devin-HP whoopsie[1382]: online
Oct 31 16:56:06  whoopsie[1382]: last message repeated 2 times
Oct 31 16:57:35 Devin-HP whoopsie[1382]: online
Oct 31 16:58:36  whoopsie[1382]: last message repeated 2 times
Oct 31 16:59:48 Devin-HP whoopsie[1382]: online
Oct 31 17:01:06  whoopsie[1382]: last message repeated 2 times
Oct 31 17:02:12 Devin-HP whoopsie[1382]: online
Oct 31 17:03:37  whoopsie[1382]: last message repeated 2 times
Oct 31 17:04:13 Devin-HP whoopsie[1382]: online
Oct 31 17:05:37  whoopsie[1382]: last message repeated 4 times
Oct 31 17:08:21 Devin-HP whoopsie[1382]: online
Oct 31 17:09:50 Devin-HP whoopsie[1382]: online
Oct 31 17:11:07  whoopsie[1382]: last message repeated 3 times
Oct 31 17:12:07  whoopsie[1382]: last message repeated 4 times
Oct 31 17:14:35 Devin-HP whoopsie[1382]: online
Oct 31 17:15:37  whoopsie[1382]: last message repeated 2 times
Oct 31 17:16:57 Devin-HP whoopsie[1382]: online
Oct 31 17:17:01 Devin-HP CRON[19361]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 31 17:18:23 Devin-HP whoopsie[1382]: online
Oct 31 17:19:37  whoopsie[1382]: last message repeated 2 times
Oct 31 17:20:37  whoopsie[1382]: last message repeated 3 times
Oct 31 17:21:42 Devin-HP whoopsie[1382]: online
Oct 31 17:21:43 Devin-HP whoopsie[1382]: online
Oct 31 17:24:04 Devin-HP whoopsie[1382]: online
Oct 31 17:25:08  whoopsie[1382]: last message repeated 3 times
Oct 31 17:26:08  whoopsie[1382]: last message repeated 2 times
Oct 31 17:27:53 Devin-HP whoopsie[1382]: online
Oct 31 17:29:08  whoopsie[1382]: last message repeated 4 times
Oct 31 17:30:08  whoopsie[1382]: last message repeated 5 times
Oct 31 17:31:08  whoopsie[1382]: last message repeated 7 times
Oct 31 17:32:08  whoopsie[1382]: last message repeated 5 times
Oct 31 17:33:08  whoopsie[1382]: last message repeated 2 times
Oct 31 17:38:18 Devin-HP whoopsie[1382]: online
Oct 31 17:39:26  whoopsie[1382]: last message repeated 4 times
Oct 31 17:40:38  whoopsie[1382]: last message repeated 3 times
Oct 31 17:41:38  whoopsie[1382]: last message repeated 2 times
Oct 31 17:43:49 Devin-HP whoopsie[1382]: online
Oct 31 17:44:50  whoopsie[1382]: last message repeated 3 times
Oct 31 17:45:25 Devin-HP whoopsie[1382]: online
Oct 31 17:47:25 Devin-HP whoopsie[1382]: online
Oct 31 17:48:31  whoopsie[1382]: last message repeated 2 times
Oct 31 17:49:28 Devin-HP whoopsie[1382]: online
Oct 31 17:50:39  whoopsie[1382]: last message repeated 2 times
Oct 31 17:51:39  whoopsie[1382]: last message repeated 2 times
Oct 31 17:52:32 Devin-HP whoopsie[1382]: online
Oct 31 17:53:07 Devin-HP whoopsie[1382]: online
Oct 31 17:54:32 Devin-HP whoopsie[1382]: online
Oct 31 17:55:33  whoopsie[1382]: last message repeated 3 times
Oct 31 17:58:34 Devin-HP whoopsie[1382]: online
Oct 31 17:59:39  whoopsie[1382]: last message repeated 2 times
Oct 31 18:00:39  whoopsie[1382]: last message repeated 2 times
Oct 31 18:01:19  whoopsie[1382]: last message repeated 2 times
Oct 31 18:01:19 Devin-HP gnome-screensaver-dialog: pam_ecryptfs: seteuid error
Oct 31 18:01:20 Devin-HP dbus[992]: [system] Activating service name='org.freedesktop.hostname1' (using servicehelper)
Oct 31 18:01:20 Devin-HP dbus[992]: [system] Successfully activated service 'org.freedesktop.hostname1'
Oct 31 18:03:19 Devin-HP whoopsie[1382]: online
Oct 31 18:04:20  whoopsie[1382]: last message repeated 3 times
Oct 31 18:04:33 Devin-HP signond[19916]: ../../../../src/signond/signondaemon.cpp 388 init Failed to SUID root. Secure storage will not be available. 
Oct 31 18:04:33 Devin-HP signond[19916]: ../../../../src/signond/credentialsaccessmanager.cpp 211 init Couldn't load AccessControlManager: "apparmor-ac" 
Oct 31 18:04:49 Devin-HP whoopsie[1382]: online
Oct 31 18:04:50 Devin-HP whoopsie[1382]: online
Oct 31 18:06:46 Devin-HP whoopsie[1382]: online
Oct 31 18:07:13 Devin-HP sudo: pam_ecryptfs: pam_sm_authenticate: /home/devin is already mounted
Oct 31 18:07:27 Devin-HP signond[20264]: ../../../../src/signond/signondaemon.cpp 388 init Failed to SUID root. Secure storage will not be available. 
Oct 31 18:07:27 Devin-HP signond[20264]: ../../../../src/signond/credentialsaccessmanager.cpp 211 init Couldn't load AccessControlManager: "apparmor-ac" 
Oct 31 18:08:33 Devin-HP whoopsie[1382]: online
Oct 31 18:09:13  whoopsie[1382]: last message repeated 3 times
Oct 31 18:09:13 Devin-HP NetworkManager[1071]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted
Oct 31 18:09:46 Devin-HP whoopsie[1382]: online
Oct 31 18:09:47 Devin-HP whoopsie[1382]: online
Oct 31 18:10:07 Devin-HP signond[20493]: ../../../../src/signond/signondaemon.cpp 388 init Failed to SUID root. Secure storage will not be available. 
Oct 31 18:10:07 Devin-HP signond[20493]: ../../../../src/signond/credentialsaccessmanager.cpp 211 init Couldn't load AccessControlManager: "apparmor-ac" 
Oct 31 18:10:16 Devin-HP whoopsie[1382]: online
Oct 31 18:10:17 Devin-HP whoopsie[1382]: online
Oct 31 18:12:37 Devin-HP kernel: [515358.253898] usb 1-1.5: new high-speed USB device number 7 using ehci-pci
Oct 31 18:12:37 Devin-HP kernel: [515358.361209] usb 1-1.5: New USB device found, idVendor=0bda, idProduct=0158
Oct 31 18:12:37 Devin-HP kernel: [515358.361219] usb 1-1.5: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Oct 31 18:12:37 Devin-HP kernel: [515358.361225] usb 1-1.5: Product: USB2.0-CRW
Oct 31 18:12:37 Devin-HP kernel: [515358.361229] usb 1-1.5: Manufacturer: Generic
Oct 31 18:12:37 Devin-HP kernel: [515358.361234] usb 1-1.5: SerialNumber: 20071114173400000
Oct 31 18:12:37 Devin-HP kernel: [515358.366384] ums-realtek 1-1.5:1.0: USB Mass Storage device detected
Oct 31 18:12:37 Devin-HP kernel: [515358.377421] scsi9 : usb-storage 1-1.5:1.0
Oct 31 18:12:38 Devin-HP mtp-probe: checking bus 1, device 7: "/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5"
Oct 31 18:12:38 Devin-HP mtp-probe: bus: 1, device: 7 was not an MTP device
Oct 31 18:12:38 Devin-HP kernel: [515359.379801] scsi 9:0:0:0: Direct-Access     Generic- Multi-Card       1.00 PQ: 0 ANSI: 0 CCS
Oct 31 18:12:38 Devin-HP kernel: [515359.380160] sd 9:0:0:0: Attached scsi generic sg2 type 0
Oct 31 18:12:39 Devin-HP kernel: [515360.073837] sd 9:0:0:0: [sdb] 7862272 512-byte logical blocks: (4.02 GB/3.74 GiB)
Oct 31 18:12:39 Devin-HP kernel: [515360.074753] sd 9:0:0:0: [sdb] Write Protect is off
Oct 31 18:12:39 Devin-HP kernel: [515360.074761] sd 9:0:0:0: [sdb] Mode Sense: 03 00 00 00
Oct 31 18:12:39 Devin-HP kernel: [515360.075880] sd 9:0:0:0: [sdb] No Caching mode page found
Oct 31 18:12:39 Devin-HP kernel: [515360.075887] sd 9:0:0:0: [sdb] Assuming drive cache: write through
Oct 31 18:12:39 Devin-HP kernel: [515360.079988] sd 9:0:0:0: [sdb] No Caching mode page found
Oct 31 18:12:39 Devin-HP kernel: [515360.079999] sd 9:0:0:0: [sdb] Assuming drive cache: write through
Oct 31 18:12:39 Devin-HP kernel: [515360.080974]  sdb: sdb1
Oct 31 18:12:39 Devin-HP kernel: [515360.084607] sd 9:0:0:0: [sdb] No Caching mode page found
Oct 31 18:12:39 Devin-HP kernel: [515360.084619] sd 9:0:0:0: [sdb] Assuming drive cache: write through
Oct 31 18:12:39 Devin-HP kernel: [515360.084624] sd 9:0:0:0: [sdb] Attached SCSI removable disk
Oct 31 18:12:41 Devin-HP udisksd[2426]: Mounted /dev/sdb1 at /media/devin/disk on behalf of uid 1000
Oct 31 18:13:36 Devin-HP whoopsie[1382]: online
Oct 31 18:14:40  whoopsie[1382]: last message repeated 3 times
Oct 31 18:15:40  whoopsie[1382]: last message repeated 2 times
Oct 31 18:17:05 Devin-HP CRON[21103]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 31 18:17:47 Devin-HP whoopsie[1382]: online
Oct 31 18:18:48  whoopsie[1382]: last message repeated 3 times
Oct 31 18:20:06  whoopsie[1382]: last message repeated 4 times
Oct 31 18:21:10  whoopsie[1382]: last message repeated 2 times
Oct 31 18:21:23 Devin-HP gnome-screensaver-dialog: pam_ecryptfs: seteuid error
Oct 31 18:22:07 Devin-HP whoopsie[1382]: online
Oct 31 18:23:10  whoopsie[1382]: last message repeated 2 times
Oct 31 18:24:11  whoopsie[1382]: last message repeated 2 times
Oct 31 18:24:13 Devin-HP whoopsie[1382]: online
Oct 31 18:25:14  whoopsie[1382]: last message repeated 2 times
Oct 31 18:27:35 Devin-HP whoopsie[1382]: online
Oct 31 18:28:41  whoopsie[1382]: last message repeated 3 times
Oct 31 18:29:41  whoopsie[1382]: last message repeated 4 times
Oct 31 18:30:41  whoopsie[1382]: last message repeated 5 times
Oct 31 18:31:41  whoopsie[1382]: last message repeated 2 times
Oct 31 18:35:14 Devin-HP whoopsie[1382]: online
Oct 31 18:36:11 Devin-HP dbus[992]: [system] Activating service name='org.freedesktop.hostname1' (using servicehelper)
Oct 31 18:36:13 Devin-HP dbus[992]: [system] Successfully activated service 'org.freedesktop.hostname1'
Oct 31 18:37:19 Devin-HP whoopsie[1382]: online
Oct 31 18:37:20 Devin-HP whoopsie[1382]: online
Oct 31 18:38:44 Devin-HP whoopsie[1382]: online
Oct 31 18:40:02  whoopsie[1382]: last message repeated 3 times
Oct 31 18:41:12  whoopsie[1382]: last message repeated 4 times
Oct 31 18:41:30 Devin-HP whoopsie[1382]: online
Oct 31 18:41:37 Devin-HP udisksd[2426]: Cleaning up mount point /media/devin/disk (device 8:17 is not mounted)
Oct 31 18:41:38 Devin-HP udisksd[2426]: Unmounted /dev/sdb1 on behalf of uid 1000
Oct 31 18:41:39 Devin-HP kernel: [517099.908358] sdb: detected capacity change from 4025483264 to 0
Oct 31 18:41:41 Devin-HP kernel: [517102.078377] usb 1-1.5: USB disconnect, device number 7
Oct 31 18:42:22 Devin-HP whoopsie[1382]: online
Oct 31 18:43:42  whoopsie[1382]: last message repeated 3 times
Oct 31 18:44:42  whoopsie[1382]: last message repeated 5 times
Oct 31 18:45:42  whoopsie[1382]: last message repeated 2 times
Oct 31 18:48:46 Devin-HP whoopsie[1382]: online
Oct 31 18:49:14 Devin-HP NetworkManager[1071]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted
Oct 31 18:49:29 Devin-HP whoopsie[1382]: online
Oct 31 18:50:42  whoopsie[1382]: last message repeated 3 times
Oct 31 18:51:42  whoopsie[1382]: last message repeated 4 times
Oct 31 18:56:36 Devin-HP whoopsie[1382]: online
Oct 31 18:57:32 Devin-HP dbus[992]: [system] Activating service name='org.freedesktop.hostname1' (using servicehelper)
Oct 31 18:57:32 Devin-HP dbus[992]: [system] Successfully activated service 'org.freedesktop.hostname1'
Oct 31 18:57:52 Devin-HP whoopsie[1382]: online
Oct 31 18:59:05  whoopsie[1382]: last message repeated 4 times
Oct 31 18:59:06 Devin-HP whoopsie[1382]: online
Oct 31 19:00:35 Devin-HP whoopsie[1382]: online
Oct 31 19:00:36 Devin-HP whoopsie[1382]: online
Oct 31 19:03:38 Devin-HP whoopsie[1382]: online
Oct 31 19:04:43  whoopsie[1382]: last message repeated 2 times
Oct 31 19:05:43  whoopsie[1382]: last message repeated 4 times
Oct 31 19:08:52 Devin-HP whoopsie[1382]: online
Oct 31 19:10:21 Devin-HP whoopsie[1382]: online
Oct 31 19:11:43  whoopsie[1382]: last message repeated 4 times
Oct 31 19:12:43  whoopsie[1382]: last message repeated 4 times
Oct 31 19:13:43  whoopsie[1382]: last message repeated 2 times
Oct 31 19:17:02 Devin-HP CRON[22608]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 31 19:17:56 Devin-HP whoopsie[1382]: online
Oct 31 19:18:54 Devin-HP whoopsie[1382]: online
Oct 31 19:19:13 Devin-HP NetworkManager[1071]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted
Oct 31 19:19:56 Devin-HP whoopsie[1382]: online
Oct 31 19:21:14  whoopsie[1382]: last message repeated 3 times
Oct 31 19:24:14 Devin-HP whoopsie[1382]: online
Oct 31 19:25:14  whoopsie[1382]: last message repeated 2 times
Oct 31 19:25:14 Devin-HP whoopsie[1382]: online
Oct 31 19:26:43 Devin-HP whoopsie[1382]: online
Oct 31 19:26:44 Devin-HP whoopsie[1382]: online
Oct 31 19:28:57 Devin-HP whoopsie[1382]: online
Oct 31 19:30:26 Devin-HP whoopsie[1382]: online
Oct 31 19:30:27 Devin-HP whoopsie[1382]: online
Oct 31 19:30:50 Devin-HP gnome-screensaver-dialog: pam_ecryptfs: seteuid error
Oct 31 19:32:11 Devin-HP whoopsie[1382]: online
Oct 31 19:34:10 Devin-HP whoopsie[1382]: online
Oct 31 19:34:11 Devin-HP whoopsie[1382]: online
Oct 31 19:38:21 Devin-HP whoopsie[1382]: online
Oct 31 19:39:45  whoopsie[1382]: last message repeated 4 times
Oct 31 19:40:45  whoopsie[1382]: last message repeated 5 times
Oct 31 19:41:45  whoopsie[1382]: last message repeated 4 times
Oct 31 19:44:14 Devin-HP whoopsie[1382]: online
Oct 31 19:45:15  whoopsie[1382]: last message repeated 2 times
Oct 31 19:46:25 Devin-HP whoopsie[1382]: online
Oct 31 19:48:24 Devin-HP whoopsie[1382]: online
Oct 31 19:49:45  whoopsie[1382]: last message repeated 2 times
Oct 31 19:50:45  whoopsie[1382]: last message repeated 3 times
Oct 31 19:51:14  whoopsie[1382]: last message repeated 2 times
Oct 31 19:51:14 Devin-HP NetworkManager[1071]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted
Oct 31 19:53:32 Devin-HP whoopsie[1382]: online
Oct 31 19:55:31 Devin-HP whoopsie[1382]: online
Oct 31 19:55:32 Devin-HP whoopsie[1382]: online
Oct 31 19:59:05 Devin-HP whoopsie[1382]: online
Oct 31 20:00:34 Devin-HP whoopsie[1382]: online
Oct 31 20:01:46  whoopsie[1382]: last message repeated 2 times
Oct 31 20:02:46  whoopsie[1382]: last message repeated 4 times
Oct 31 20:03:46  whoopsie[1382]: last message repeated 2 times
Oct 31 20:04:14 Devin-HP whoopsie[1382]: online
Oct 31 20:05:16  whoopsie[1382]: last message repeated 2 times
Oct 31 20:07:13 Devin-HP NetworkManager[1071]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted
Oct 31 20:07:46 Devin-HP whoopsie[1382]: online
Oct 31 20:08:41 Devin-HP whoopsie[1382]: online
Oct 31 20:09:45  whoopsie[1382]: last message repeated 3 times
Oct 31 20:09:46 Devin-HP whoopsie[1382]: online
Oct 31 20:17:01 Devin-HP CRON[22808]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 31 20:26:05 Devin-HP whoopsie[1382]: online
Oct 31 20:27:17  whoopsie[1382]: last message repeated 3 times
Oct 31 20:37:26 Devin-HP gnome-screensaver-dialog: pam_ecryptfs: seteuid error
Oct 31 20:37:41 Devin-HP signond[22931]: ../../../../src/signond/signondaemon.cpp 388 init Failed to SUID root. Secure storage will not be available. 
Oct 31 20:37:42 Devin-HP signond[22931]: ../../../../src/signond/credentialsaccessmanager.cpp 211 init Couldn't load AccessControlManager: "apparmor-ac" 
Oct 31 20:49:13 Devin-HP NetworkManager[1071]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted
Oct 31 20:50:12 Devin-HP whoopsie[1382]: online
Oct 31 20:51:18  whoopsie[1382]: last message repeated 2 times
Oct 31 21:02:31 Devin-HP gnome-screensaver-dialog: pam_ecryptfs: seteuid error
Oct 31 21:02:33 Devin-HP dbus[992]: [system] Activating service name='org.freedesktop.hostname1' (using servicehelper)
Oct 31 21:02:33 Devin-HP dbus[992]: [system] Successfully activated service 'org.freedesktop.hostname1'
Oct 31 21:03:13 Devin-HP NetworkManager[1071]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted
Oct 31 21:03:52 Devin-HP whoopsie[1382]: online
Oct 31 21:05:18  whoopsie[1382]: last message repeated 2 times
Oct 31 21:17:01 Devin-HP CRON[23535]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 31 21:41:13 Devin-HP NetworkManager[1071]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted
Oct 31 21:41:49 Devin-HP gnome-screensaver-dialog: pam_ecryptfs: seteuid error
Oct 31 21:50:12 Devin-HP whoopsie[1382]: online
Oct 31 21:51:20  whoopsie[1382]: last message repeated 2 times
Oct 31 21:59:13 Devin-HP NetworkManager[1071]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted
Oct 31 22:01:08 Devin-HP whoopsie[1382]: online
Oct 31 22:01:13 Devin-HP NetworkManager[1071]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted
Oct 31 22:01:15 Devin-HP whoopsie[1382]: online
Oct 31 22:02:37 Devin-HP whoopsie[1382]: online
Oct 31 22:02:38 Devin-HP whoopsie[1382]: online
Oct 31 22:07:17 Devin-HP gnome-screensaver-dialog: pam_ecryptfs: seteuid error
Oct 31 22:11:13 Devin-HP NetworkManager[1071]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted
Oct 31 22:11:35 Devin-HP signond[24171]: ../../../../src/signond/signondaemon.cpp 388 init Failed to SUID root. Secure storage will not be available. 
Oct 31 22:11:35 Devin-HP signond[24171]: ../../../../src/signond/credentialsaccessmanager.cpp 211 init Couldn't load AccessControlManager: "apparmor-ac" 
Oct 31 22:17:08 Devin-HP CRON[24390]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 31 22:31:13 Devin-HP NetworkManager[1071]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted
Oct 31 22:33:31 Devin-HP dbus[992]: [system] Activating service name='org.freedesktop.hostname1' (using servicehelper)
Oct 31 22:33:32 Devin-HP dbus[992]: [system] Successfully activated service 'org.freedesktop.hostname1'
Oct 31 22:44:00 Devin-HP dbus[992]: [system] Activating service name='org.freedesktop.hostname1' (using servicehelper)
Oct 31 22:44:02 Devin-HP dbus[992]: [system] Successfully activated service 'org.freedesktop.hostname1'
Oct 31 22:50:13 Devin-HP whoopsie[1382]: online
Oct 31 22:51:23  whoopsie[1382]: last message repeated 2 times
Oct 31 22:54:39 Devin-HP kernel: [532273.651813] window-stack-br[2122]: segfault at 8 ip 00007f2964cf3bd4 sp 00007fff58ecd1d0 error 4 in libQt5DBus.so.5.0.2[7f2964cc4000+73000]
Oct 31 23:00:17 Devin-HP signond[25672]: ../../../../src/signond/signondaemon.cpp 388 init Failed to SUID root. Secure storage will not be available. 
Oct 31 23:00:18 Devin-HP signond[25672]: ../../../../src/signond/credentialsaccessmanager.cpp 211 init Couldn't load AccessControlManager: "apparmor-ac" 
Oct 31 23:00:56 Devin-HP signond[25672]: The signon plugin does not react on demand to stop: need to kill it!!! 
Oct 31 23:00:56 Devin-HP signond[25672]: Challenge produces CRASH! 
Oct 31 23:03:13 Devin-HP NetworkManager[1071]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted
Oct 31 23:08:03 Devin-HP dbus[992]: [system] Activating service name='org.freedesktop.hostname1' (using servicehelper)
Oct 31 23:08:04 Devin-HP dbus[992]: [system] Successfully activated service 'org.freedesktop.hostname1'
Oct 31 23:17:03 Devin-HP CRON[26344]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 31 23:19:13 Devin-HP NetworkManager[1071]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted
Oct 31 23:37:57 Devin-HP kernel: [534870.555487] CPU1: Core temperature above threshold, cpu clock throttled (total events = 1)
Oct 31 23:37:57 Devin-HP kernel: [534870.555492] CPU0: Core temperature above threshold, cpu clock throttled (total events = 1)
Oct 31 23:37:57 Devin-HP kernel: [534870.556532] CPU0: Core temperature/speed normal
Oct 31 23:37:57 Devin-HP kernel: [534870.556533] CPU1: Core temperature/speed normal
Oct 31 23:39:13 Devin-HP NetworkManager[1071]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted
Oct 31 23:39:41 Devin-HP kernel: [534974.080922] mce: [Hardware Error]: Machine check events logged
Oct 31 23:45:13 Devin-HP NetworkManager[1071]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted
Oct 31 23:47:27 Devin-HP kernel: [535440.402039] CPU1: Core temperature above threshold, cpu clock throttled (total events = 17)
Oct 31 23:47:27 Devin-HP kernel: [535440.402045] CPU0: Core temperature above threshold, cpu clock throttled (total events = 17)
Oct 31 23:47:27 Devin-HP kernel: [535440.403088] CPU0: Core temperature/speed normal
Oct 31 23:47:27 Devin-HP kernel: [535440.403089] CPU1: Core temperature/speed normal
Oct 31 23:49:13 Devin-HP NetworkManager[1071]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted
Oct 31 23:50:12 Devin-HP whoopsie[1382]: online
Oct 31 23:51:26  whoopsie[1382]: last message repeated 2 times
Oct 31 23:51:50 Devin-HP kernel: [535702.737032] mce: [Hardware Error]: Machine check events logged
Oct 31 23:52:33 Devin-HP kernel: [535745.967882] CPU0: Core temperature above threshold, cpu clock throttled (total events = 56)
Oct 31 23:52:33 Devin-HP kernel: [535745.967884] CPU1: Core temperature above threshold, cpu clock throttled (total events = 56)
Oct 31 23:52:33 Devin-HP kernel: [535745.968933] CPU0: Core temperature/speed normal
Oct 31 23:52:33 Devin-HP kernel: [535745.968934] CPU1: Core temperature/speed normal
Oct 31 23:54:20 Devin-HP kernel: [535852.673682] mce: [Hardware Error]: Machine check events logged
Nov  1 00:01:10 Devin-HP kernel: [536262.392065] CPU0: Core temperature above threshold, cpu clock throttled (total events = 93)
Nov  1 00:01:10 Devin-HP kernel: [536262.392067] CPU1: Core temperature above threshold, cpu clock throttled (total events = 93)
Nov  1 00:01:10 Devin-HP kernel: [536262.393097] CPU1: Core temperature/speed normal
Nov  1 00:01:10 Devin-HP kernel: [536262.393098] CPU0: Core temperature/speed normal
Nov  1 00:01:50 Devin-HP kernel: [536302.495649] mce: [Hardware Error]: Machine check events logged
Nov  1 00:07:33 Devin-HP kernel: [536645.644824] CPU0: Core temperature above threshold, cpu clock throttled (total events = 96)
Nov  1 00:07:33 Devin-HP kernel: [536645.644830] CPU1: Core temperature above threshold, cpu clock throttled (total events = 96)
Nov  1 00:07:33 Devin-HP kernel: [536645.645868] CPU0: Core temperature/speed normal
Nov  1 00:07:33 Devin-HP kernel: [536645.645869] CPU1: Core temperature/speed normal
Nov  1 00:08:05 Devin-HP kernel: [536677.325263] mce: [Hardware Error]: Machine check events logged
Nov  1 00:13:45 Devin-HP kernel: [537017.019251] CPU3: Core temperature above threshold, cpu clock throttled (total events = 15)
Nov  1 00:13:45 Devin-HP kernel: [537017.019257] CPU2: Core temperature above threshold, cpu clock throttled (total events = 15)
Nov  1 00:13:45 Devin-HP kernel: [537017.020299] CPU3: Core temperature/speed normal
Nov  1 00:13:45 Devin-HP kernel: [537017.020300] CPU2: Core temperature/speed normal
Nov  1 00:14:20 Devin-HP kernel: [537052.178887] mce: [Hardware Error]: Machine check events logged
Nov  1 00:17:04 Devin-HP CRON[26472]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov  1 00:23:05 Devin-HP kernel: [537576.623202] CPU1: Core temperature above threshold, cpu clock throttled (total events = 121)
Nov  1 00:23:05 Devin-HP kernel: [537576.623208] CPU0: Core temperature above threshold, cpu clock throttled (total events = 121)
Nov  1 00:23:05 Devin-HP kernel: [537576.624247] CPU0: Core temperature/speed normal
Nov  1 00:23:05 Devin-HP kernel: [537576.624248] CPU1: Core temperature/speed normal
Nov  1 00:25:35 Devin-HP kernel: [537726.881751] mce: [Hardware Error]: Machine check events logged
Nov  1 00:32:47 Devin-HP kernel: [538159.204389] CPU0: Core temperature above threshold, cpu clock throttled (total events = 224)
Nov  1 00:32:47 Devin-HP kernel: [538159.204391] CPU1: Core temperature above threshold, cpu clock throttled (total events = 224)
Nov  1 00:32:47 Devin-HP kernel: [538159.205438] CPU1: Core temperature/speed normal
Nov  1 00:32:47 Devin-HP kernel: [538159.205439] CPU0: Core temperature/speed normal
Nov  1 00:33:05 Devin-HP kernel: [538176.691662] mce: [Hardware Error]: Machine check events logged
Nov  1 00:42:29 Devin-HP kernel: [538740.388968] CPU3: Core temperature above threshold, cpu clock throttled (total events = 172)
Nov  1 00:42:29 Devin-HP kernel: [538740.388974] CPU2: Core temperature above threshold, cpu clock throttled (total events = 172)
Nov  1 00:42:29 Devin-HP kernel: [538740.390017] CPU3: Core temperature/speed normal
Nov  1 00:42:29 Devin-HP kernel: [538740.390018] CPU2: Core temperature/speed normal
Nov  1 00:49:11 Devin-HP kernel: [539142.241328] CPU3: Core temperature above threshold, cpu clock throttled (total events = 177)
Nov  1 00:49:11 Devin-HP kernel: [539142.241330] CPU2: Core temperature above threshold, cpu clock throttled (total events = 177)
Nov  1 00:49:11 Devin-HP kernel: [539142.242373] CPU3: Core temperature/speed normal
Nov  1 00:49:11 Devin-HP kernel: [539142.242373] CPU2: Core temperature/speed normal
Nov  1 00:50:12 Devin-HP whoopsie[1382]: online
Nov  1 00:51:31  whoopsie[1382]: last message repeated 2 times
Nov  1 00:57:36 Devin-HP kernel: [539647.451889] CPU3: Core temperature above threshold, cpu clock throttled (total events = 312)
Nov  1 00:57:36 Devin-HP kernel: [539647.451894] CPU2: Core temperature above threshold, cpu clock throttled (total events = 312)
Nov  1 00:57:36 Devin-HP kernel: [539647.452939] CPU3: Core temperature/speed normal
Nov  1 00:57:36 Devin-HP kernel: [539647.452940] CPU2: Core temperature/speed normal
Nov  1 01:02:51 Devin-HP kernel: [539962.426124] CPU1: Core temperature above threshold, cpu clock throttled (total events = 514)
Nov  1 01:02:51 Devin-HP kernel: [539962.426125] CPU0: Core temperature above threshold, cpu clock throttled (total events = 514)
Nov  1 01:02:51 Devin-HP kernel: [539962.427174] CPU1: Core temperature/speed normal
Nov  1 01:02:51 Devin-HP kernel: [539962.427175] CPU0: Core temperature/speed normal
Nov  1 01:13:18 Devin-HP kernel: [540588.830002] CPU0: Core temperature above threshold, cpu clock throttled (total events = 529)
Nov  1 01:13:18 Devin-HP kernel: [540588.830004] CPU1: Core temperature above threshold, cpu clock throttled (total events = 529)
Nov  1 01:13:18 Devin-HP kernel: [540588.831053] CPU0: Core temperature/speed normal
Nov  1 01:13:18 Devin-HP kernel: [540588.831054] CPU1: Core temperature/speed normal
Nov  1 01:17:05 Devin-HP CRON[26590]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov  1 01:18:22 Devin-HP kernel: [540892.639964] CPU0: Core temperature above threshold, cpu clock throttled (total events = 546)
Nov  1 01:18:22 Devin-HP kernel: [540892.639970] CPU1: Core temperature above threshold, cpu clock throttled (total events = 546)
Nov  1 01:18:22 Devin-HP kernel: [540892.641013] CPU0: Core temperature/speed normal
Nov  1 01:18:22 Devin-HP kernel: [540892.641014] CPU1: Core temperature/speed normal
Nov  1 01:42:45 Devin-HP kernel: [542354.588986] CPU0: Core temperature above threshold, cpu clock throttled (total events = 605)
Nov  1 01:42:45 Devin-HP kernel: [542354.588987] CPU1: Core temperature above threshold, cpu clock throttled (total events = 605)
Nov  1 01:42:45 Devin-HP kernel: [542354.590036] CPU0: Core temperature/speed normal
Nov  1 01:42:45 Devin-HP kernel: [542354.590037] CPU1: Core temperature/speed normal
Nov  1 01:48:42 Devin-HP kernel: [542712.128835] CPU0: Core temperature above threshold, cpu clock throttled (total events = 614)
Nov  1 01:48:42 Devin-HP kernel: [542712.128840] CPU1: Core temperature above threshold, cpu clock throttled (total events = 614)
Nov  1 01:48:42 Devin-HP kernel: [542712.129877] CPU1: Core temperature/speed normal
Nov  1 01:48:42 Devin-HP kernel: [542712.129883] CPU0: Core temperature/speed normal
Nov  1 01:50:14 Devin-HP whoopsie[1382]: online
Nov  1 01:51:34  whoopsie[1382]: last message repeated 2 times
Nov  1 01:55:31 Devin-HP wpa_supplicant[1147]: wlan0: WPA: Group rekeying completed with [redacted] [GTK=CCMP]
Nov  1 02:07:33 Devin-HP kernel: [543842.222490] CPU1: Core temperature above threshold, cpu clock throttled (total events = 838)
Nov  1 02:07:33 Devin-HP kernel: [543842.222496] CPU0: Core temperature above threshold, cpu clock throttled (total events = 838)
Nov  1 02:07:33 Devin-HP kernel: [543842.224591] CPU1: Core temperature/speed normal
Nov  1 02:07:33 Devin-HP kernel: [543842.224592] CPU0: Core temperature/speed normal
Nov  1 02:15:55 Devin-HP kernel: [544344.320498] CPU1: Core temperature above threshold, cpu clock throttled (total events = 880)
Nov  1 02:15:55 Devin-HP kernel: [544344.320504] CPU0: Core temperature above threshold, cpu clock throttled (total events = 880)
Nov  1 02:15:55 Devin-HP kernel: [544344.321546] CPU0: Core temperature/speed normal
Nov  1 02:15:55 Devin-HP kernel: [544344.321547] CPU1: Core temperature/speed normal
Nov  1 02:17:05 Devin-HP CRON[26711]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov  1 02:19:13 Devin-HP NetworkManager[1071]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted
Nov  1 02:22:41 Devin-HP kernel: [544749.739839] CPU1: Core temperature above threshold, cpu clock throttled (total events = 899)
Nov  1 02:22:41 Devin-HP kernel: [544749.739845] CPU0: Core temperature above threshold, cpu clock throttled (total events = 899)
Nov  1 02:22:41 Devin-HP kernel: [544749.741940] CPU1: Core temperature/speed normal
Nov  1 02:22:41 Devin-HP kernel: [544749.741941] CPU0: Core temperature/speed normal
Nov  1 02:25:13 Devin-HP NetworkManager[1071]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted
Nov  1 02:28:20 Devin-HP kernel: [545089.319144] CPU0: Core temperature above threshold, cpu clock throttled (total events = 973)
Nov  1 02:28:20 Devin-HP kernel: [545089.319146] CPU1: Core temperature above threshold, cpu clock throttled (total events = 973)
Nov  1 02:28:20 Devin-HP kernel: [545089.320196] CPU1: Core temperature/speed normal
Nov  1 02:28:20 Devin-HP kernel: [545089.320197] CPU0: Core temperature/speed normal
Nov  1 02:37:08 Devin-HP kernel: [545616.392880] CPU1: Core temperature above threshold, cpu clock throttled (total events = 1064)
Nov  1 02:37:08 Devin-HP kernel: [545616.392886] CPU0: Core temperature above threshold, cpu clock throttled (total events = 1064)
Nov  1 02:37:08 Devin-HP kernel: [545616.393926] CPU1: Core temperature/speed normal
Nov  1 02:37:08 Devin-HP kernel: [545616.393927] CPU0: Core temperature/speed normal
Nov  1 02:41:13 Devin-HP NetworkManager[1071]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted
Nov  1 02:49:01 Devin-HP kernel: [546329.765397] CPU0: Core temperature above threshold, cpu clock throttled (total events = 1081)
Nov  1 02:49:01 Devin-HP kernel: [546329.765399] CPU1: Core temperature above threshold, cpu clock throttled (total events = 1081)
Nov  1 02:49:01 Devin-HP kernel: [546329.766447] CPU0: Core temperature/speed normal
Nov  1 02:49:01 Devin-HP kernel: [546329.766448] CPU1: Core temperature/speed normal
Nov  1 02:50:12 Devin-HP whoopsie[1382]: online
Nov  1 02:51:37  whoopsie[1382]: last message repeated 2 times
Nov  1 02:57:26 Devin-HP kernel: [546834.322332] CPU0: Core temperature above threshold, cpu clock throttled (total events = 1105)
Nov  1 02:57:26 Devin-HP kernel: [546834.322337] CPU1: Core temperature above threshold, cpu clock throttled (total events = 1105)
Nov  1 02:57:26 Devin-HP kernel: [546834.323379] CPU1: Core temperature/speed normal
Nov  1 02:57:26 Devin-HP kernel: [546834.323379] CPU0: Core temperature/speed normal
Nov  1 03:17:04 Devin-HP CRON[26830]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov  1 03:23:17 Devin-HP kernel: [548384.530133] cfg80211: Calling CRDA to update world regulatory domain
Nov  1 03:23:17 Devin-HP wpa_supplicant[1147]: wlan0: CTRL-EVENT-DISCONNECTED bssid=20:e5:2a:60:b0:7e reason=4
Nov  1 03:23:18 Devin-HP NetworkManager[1071]: <info> (wlan0): supplicant interface state: completed -> scanning
Nov  1 03:23:18 Devin-HP kernel: [548385.874481] wlan0: authenticate with [redacted]
Nov  1 03:23:18 Devin-HP wpa_supplicant[1147]: wlan0: SME: Trying to authenticate with [redacted] (SSID='NETGEAR23' freq=2437 MHz)
Nov  1 03:23:18 Devin-HP NetworkManager[1071]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Nov  1 03:23:18 Devin-HP wpa_supplicant[1147]: wlan0: Trying to associate with [redacted] (SSID='NETGEAR23' freq=2437 MHz)
Nov  1 03:23:18 Devin-HP kernel: [548385.897860] wlan0: send auth to [redacted] (try 1/3)
Nov  1 03:23:18 Devin-HP kernel: [548385.899927] wlan0: authenticated
Nov  1 03:23:18 Devin-HP kernel: [548385.901826] wlan0: associate with [redacted] (try 1/3)
Nov  1 03:23:18 Devin-HP NetworkManager[1071]: <info> (wlan0): supplicant interface state: authenticating -> associating
Nov  1 03:23:18 Devin-HP wpa_supplicant[1147]: wlan0: Associated with [redacted]
Nov  1 03:23:18 Devin-HP kernel: [548385.906077] wlan0: RX AssocResp from [redacted] (capab=0x431 status=0 aid=2)
Nov  1 03:23:18 Devin-HP kernel: [548385.906153] wlan0: associated
Nov  1 03:23:18 Devin-HP NetworkManager[1071]: <info> (wlan0): supplicant interface state: associating -> associated
Nov  1 03:23:18 Devin-HP NetworkManager[1071]: <info> (wlan0): supplicant interface state: associated -> 4-way handshake
Nov  1 03:23:20 Devin-HP kernel: [548387.240361] cfg80211: World regulatory domain updated:
Nov  1 03:23:20 Devin-HP kernel: [548387.240367] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Nov  1 03:23:20 Devin-HP kernel: [548387.240370] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov  1 03:23:20 Devin-HP kernel: [548387.240373] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov  1 03:23:20 Devin-HP kernel: [548387.240375] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Nov  1 03:23:20 Devin-HP kernel: [548387.240378] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov  1 03:23:20 Devin-HP kernel: [548387.240380] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov  1 03:23:21 Devin-HP wpa_supplicant[1147]: wlan0: WPA: Key negotiation completed with [redacted] [PTK=CCMP GTK=CCMP]
Nov  1 03:23:21 Devin-HP wpa_supplicant[1147]: wlan0: CTRL-EVENT-CONNECTED - Connection to [redacted] completed (reauth) [id=0 id_str=]
Nov  1 03:23:22 Devin-HP NetworkManager[1071]: <info> (wlan0): supplicant interface state: 4-way handshake -> completed
Nov  1 03:32:02 Devin-HP whoopsie[1382]: online
Nov  1 03:33:09  whoopsie[1382]: last message repeated 3 times
Nov  1 03:33:15 Devin-HP wpa_supplicant[1147]: wlan0: CTRL-EVENT-DISCONNECTED bssid=[redacted] reason=4
Nov  1 03:33:15 Devin-HP kernel: [548982.217641] cfg80211: Calling CRDA to update world regulatory domain
Nov  1 03:33:15 Devin-HP NetworkManager[1071]: <info> (wlan0): supplicant interface state: completed -> disconnected
Nov  1 03:33:15 Devin-HP NetworkManager[1071]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Nov  1 03:33:16 Devin-HP wpa_supplicant[1147]: wlan0: SME: Trying to authenticate with [redacted] (SSID='NETGEAR23' freq=2437 MHz)
Nov  1 03:33:16 Devin-HP kernel: [548982.930114] wlan0: authenticate with [redacted]
Nov  1 03:33:16 Devin-HP NetworkManager[1071]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Nov  1 03:33:16 Devin-HP kernel: [548982.952790] wlan0: send auth to [redacted] (try 1/3)
Nov  1 03:33:16 Devin-HP wpa_supplicant[1147]: wlan0: Trying to associate with [redacted] (SSID='NETGEAR23' freq=2437 MHz)
Nov  1 03:33:16 Devin-HP kernel: [548982.954837] wlan0: authenticated
Nov  1 03:33:16 Devin-HP kernel: [548982.957523] wlan0: associate with [redacted] (try 1/3)
Nov  1 03:33:16 Devin-HP NetworkManager[1071]: <info> (wlan0): supplicant interface state: authenticating -> associating
Nov  1 03:33:16 Devin-HP wpa_supplicant[1147]: wlan0: Associated with [redacted]
Nov  1 03:33:16 Devin-HP kernel: [548982.961808] wlan0: RX AssocResp from [redacted] (capab=0x431 status=0 aid=2)
Nov  1 03:33:16 Devin-HP kernel: [548982.961884] wlan0: associated
Nov  1 03:33:16 Devin-HP NetworkManager[1071]: <info> (wlan0): supplicant interface state: associating -> associated
Nov  1 03:33:16 Devin-HP NetworkManager[1071]: <info> (wlan0): supplicant interface state: associated -> 4-way handshake
Nov  1 03:33:16 Devin-HP wpa_supplicant[1147]: wlan0: WPA: Key negotiation completed with [redacted] [PTK=CCMP GTK=CCMP]
Nov  1 03:33:16 Devin-HP wpa_supplicant[1147]: wlan0: CTRL-EVENT-CONNECTED - Connection to [redacted] completed (reauth) [id=0 id_str=]
Nov  1 03:33:16 Devin-HP NetworkManager[1071]: <info> (wlan0): supplicant interface state: 4-way handshake -> completed
Nov  1 03:33:17 Devin-HP kernel: [548984.176132] cfg80211: World regulatory domain updated:
Nov  1 03:33:17 Devin-HP kernel: [548984.176138] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Nov  1 03:33:17 Devin-HP kernel: [548984.176140] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov  1 03:33:17 Devin-HP kernel: [548984.176142] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov  1 03:33:17 Devin-HP kernel: [548984.176144] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Nov  1 03:33:17 Devin-HP kernel: [548984.176146] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov  1 03:33:17 Devin-HP kernel: [548984.176147] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov  1 03:49:13 Devin-HP NetworkManager[1071]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted
Nov  1 03:50:12 Devin-HP whoopsie[1382]: online
Nov  1 03:51:40  whoopsie[1382]: last message repeated 2 times
Nov  1 03:59:13 Devin-HP NetworkManager[1071]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted
Nov  1 04:06:33 Devin-HP kernel: [550979.443479] CPU1: Core temperature above threshold, cpu clock throttled (total events = 1144)
Nov  1 04:06:33 Devin-HP kernel: [550979.443481] CPU0: Core temperature above threshold, cpu clock throttled (total events = 1144)
Nov  1 04:06:33 Devin-HP kernel: [550979.444531] CPU1: Core temperature/speed normal
Nov  1 04:06:33 Devin-HP kernel: [550979.444531] CPU0: Core temperature/speed normal
Nov  1 04:17:06 Devin-HP CRON[26955]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov  1 04:50:12 Devin-HP whoopsie[1382]: online
Nov  1 04:51:13  whoopsie[1382]: last message repeated 2 times
Nov  1 05:02:23 Devin-HP kernel: [554328.170081] CPU1: Core temperature above threshold, cpu clock throttled (total events = 1209)
Nov  1 05:02:23 Devin-HP kernel: [554328.170087] CPU0: Core temperature above threshold, cpu clock throttled (total events = 1209)
Nov  1 05:02:23 Devin-HP kernel: [554328.171127] CPU1: Core temperature/speed normal
Nov  1 05:02:23 Devin-HP kernel: [554328.171128] CPU0: Core temperature/speed normal
Nov  1 05:08:43 Devin-HP whoopsie[1382]: online
Nov  1 05:09:44  whoopsie[1382]: last message repeated 3 times
Nov  1 05:17:05 Devin-HP CRON[27079]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov  1 05:23:15 Devin-HP kernel: [555579.884080] cfg80211: Calling CRDA to update world regulatory domain
Nov  1 05:23:16 Devin-HP wpa_supplicant[1147]: wlan0: CTRL-EVENT-DISCONNECTED bssid=[redacted] reason=4
Nov  1 05:23:16 Devin-HP NetworkManager[1071]: <info> (wlan0): supplicant interface state: completed -> scanning
Nov  1 05:23:16 Devin-HP kernel: [555580.850513] wlan0: authenticate with [redacted]
Nov  1 05:23:16 Devin-HP wpa_supplicant[1147]: wlan0: SME: Trying to authenticate with [redacted] (SSID='NETGEAR23' freq=2437 MHz)
Nov  1 05:23:16 Devin-HP kernel: [555580.873026] wlan0: send auth to [redacted] (try 1/3)
Nov  1 05:23:16 Devin-HP NetworkManager[1071]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Nov  1 05:23:16 Devin-HP wpa_supplicant[1147]: wlan0: Trying to associate with [redacted] (SSID='NETGEAR23' freq=2437 MHz)
Nov  1 05:23:16 Devin-HP kernel: [555580.875008] wlan0: authenticated
Nov  1 05:23:16 Devin-HP kernel: [555580.877550] wlan0: associate with [redacted] (try 1/3)
Nov  1 05:23:16 Devin-HP NetworkManager[1071]: <info> (wlan0): supplicant interface state: authenticating -> associating
Nov  1 05:23:16 Devin-HP wpa_supplicant[1147]: wlan0: Associated with [redacted]
Nov  1 05:23:16 Devin-HP kernel: [555580.881797] wlan0: RX AssocResp from [redacted] (capab=0x431 status=0 aid=2)
Nov  1 05:23:16 Devin-HP kernel: [555580.881858] wlan0: associated
Nov  1 05:23:16 Devin-HP NetworkManager[1071]: <info> (wlan0): supplicant interface state: associating -> associated
Nov  1 05:23:17 Devin-HP NetworkManager[1071]: <info> (wlan0): supplicant interface state: associated -> 4-way handshake
Nov  1 05:23:17 Devin-HP wpa_supplicant[1147]: wlan0: WPA: Key negotiation completed with [redacted] [PTK=CCMP GTK=CCMP]
Nov  1 05:23:17 Devin-HP wpa_supplicant[1147]: wlan0: CTRL-EVENT-CONNECTED - Connection to [redacted] completed (reauth) [id=0 id_str=]
Nov  1 05:23:17 Devin-HP NetworkManager[1071]: <info> (wlan0): supplicant interface state: 4-way handshake -> completed
Nov  1 05:23:17 Devin-HP kernel: [555581.874904] cfg80211: World regulatory domain updated:
Nov  1 05:23:17 Devin-HP kernel: [555581.874908] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Nov  1 05:23:17 Devin-HP kernel: [555581.874910] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov  1 05:23:17 Devin-HP kernel: [555581.874912] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov  1 05:23:17 Devin-HP kernel: [555581.874914] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Nov  1 05:23:17 Devin-HP kernel: [555581.874915] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov  1 05:23:17 Devin-HP kernel: [555581.874917] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov  1 05:50:12 Devin-HP whoopsie[1382]: online
Nov  1 05:51:16  whoopsie[1382]: last message repeated 2 times
Nov  1 06:17:01 Devin-HP CRON[27197]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov  1 06:19:13 Devin-HP NetworkManager[1071]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted
Nov  1 06:25:01 Devin-HP CRON[27215]: (root) CMD (test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily ))
Nov  1 06:43:13 Devin-HP NetworkManager[1071]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted
Nov  1 06:49:42 Devin-HP whoopsie[1382]: online
Nov  1 06:50:43  whoopsie[1382]: last message repeated 4 times
Nov  1 06:52:02 Devin-HP CRON[27269]: (root) CMD (test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly ))
Nov  1 06:54:34 Devin-HP kernel: [561055.784400] usb 2-1.1: new low-speed USB device number 7 using ehci-pci
Nov  1 06:54:34 Devin-HP kernel: [561055.882110] usb 2-1.1: New USB device found, idVendor=413c, idProduct=3016
Nov  1 06:54:34 Devin-HP kernel: [561055.882119] usb 2-1.1: New USB device strings: Mfr=0, Product=2, SerialNumber=0
Nov  1 06:54:34 Devin-HP kernel: [561055.882124] usb 2-1.1: Product: Dell Premium USB Optical Mouse
Nov  1 06:54:34 Devin-HP kernel: [561055.887237] input: Dell Premium USB Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.0/input/input13
Nov  1 06:54:34 Devin-HP kernel: [561055.887434] hid-generic 0003:413C:3016.0002: input,hidraw0: USB HID v1.11 Mouse [Dell Premium USB Optical Mouse] on usb-0000:00:1d.0-1.1/input0
Nov  1 06:54:34 Devin-HP mtp-probe: checking bus 2, device 7: "/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1"
Nov  1 06:54:34 Devin-HP mtp-probe: bus: 2, device: 7 was not an MTP device
Nov  1 06:54:51 Devin-HP gnome-screensaver-dialog: pam_ecryptfs: seteuid error
Nov  1 06:54:57 Devin-HP kernel: [561079.270287] usb 2-1.2: new high-speed USB device number 8 using ehci-pci
Nov  1 06:54:57 Devin-HP kernel: [561079.363751] usb 2-1.2: New USB device found, idVendor=1058, idProduct=0740
Nov  1 06:54:57 Devin-HP kernel: [561079.363761] usb 2-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=5
Nov  1 06:54:57 Devin-HP kernel: [561079.363767] usb 2-1.2: Product: My Passport 0740
Nov  1 06:54:57 Devin-HP kernel: [561079.363772] usb 2-1.2: Manufacturer: Western Digital
Nov  1 06:54:57 Devin-HP kernel: [561079.363776] usb 2-1.2: SerialNumber: [redacted]
Nov  1 06:54:57 Devin-HP kernel: [561079.364547] usb-storage 2-1.2:1.0: USB Mass Storage device detected
Nov  1 06:54:57 Devin-HP kernel: [561079.364723] scsi10 : usb-storage 2-1.2:1.0
Nov  1 06:54:57 Devin-HP mtp-probe: checking bus 2, device 8: "/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2"
Nov  1 06:54:57 Devin-HP mtp-probe: bus: 2, device: 8 was not an MTP device
Nov  1 06:54:58 Devin-HP kernel: [561080.362698] scsi 10:0:0:0: Direct-Access     WD       My Passport 0740 1003 PQ: 0 ANSI: 6
Nov  1 06:54:58 Devin-HP kernel: [561080.363291] scsi 10:0:0:1: Enclosure         WD       SES Device       1003 PQ: 0 ANSI: 6
Nov  1 06:54:58 Devin-HP kernel: [561080.364074] sd 10:0:0:0: Attached scsi generic sg2 type 0
Nov  1 06:54:58 Devin-HP kernel: [561080.364313] ses 10:0:0:1: Attached Enclosure device
Nov  1 06:54:58 Devin-HP kernel: [561080.364496] ses 10:0:0:1: Attached scsi generic sg3 type 13
Nov  1 06:55:04 Devin-HP kernel: [561085.927831] sd 10:0:0:0: [sdb] 1953458176 512-byte logical blocks: (1.00 TB/931 GiB)
Nov  1 06:55:04 Devin-HP kernel: [561085.929850] sd 10:0:0:0: [sdb] Write Protect is off
Nov  1 06:55:04 Devin-HP kernel: [561085.929861] sd 10:0:0:0: [sdb] Mode Sense: 47 00 10 08
Nov  1 06:55:04 Devin-HP kernel: [561085.931275] sd 10:0:0:0: [sdb] No Caching mode page found
Nov  1 06:55:04 Devin-HP kernel: [561085.931285] sd 10:0:0:0: [sdb] Assuming drive cache: write through
Nov  1 06:55:04 Devin-HP kernel: [561085.936910] sd 10:0:0:0: [sdb] No Caching mode page found
Nov  1 06:55:04 Devin-HP kernel: [561085.936920] sd 10:0:0:0: [sdb] Assuming drive cache: write through
Nov  1 06:55:04 Devin-HP kernel: [561085.948670]  sdb: sdb1
Nov  1 06:55:04 Devin-HP kernel: [561085.952150] sd 10:0:0:0: [sdb] No Caching mode page found
Nov  1 06:55:04 Devin-HP kernel: [561085.952159] sd 10:0:0:0: [sdb] Assuming drive cache: write through
Nov  1 06:55:04 Devin-HP kernel: [561085.952165] sd 10:0:0:0: [sdb] Attached SCSI disk
Nov  1 06:55:07 Devin-HP ntfs-3g[27339]: Version 2013.1.13AR.1 external FUSE 29
Nov  1 06:55:07 Devin-HP ntfs-3g[27339]: Mounted /dev/sdb1 (Read-Write, label "My Passport", NTFS 3.1)
Nov  1 06:55:07 Devin-HP ntfs-3g[27339]: Cmdline options: rw,nosuid,nodev,uhelper=udisks2,uid=1000,gid=1000,dmask=0077,fmask=0177
Nov  1 06:55:07 Devin-HP ntfs-3g[27339]: Mount options: rw,nosuid,nodev,uhelper=udisks2,allow_other,nonempty,relatime,default_permissions,fsname=/dev/sdb1,blkdev,blksize=4096
Nov  1 06:55:07 Devin-HP ntfs-3g[27339]: Global ownership and permissions enforced, configuration type 7
Nov  1 06:55:07 Devin-HP udisksd[2426]: Mounted /dev/sdb1 at /media/devin/My Passport1 on behalf of uid 1000
Nov  1 06:55:09 Devin-HP dbus[992]: [system] Activating service name='org.freedesktop.hostname1' (using servicehelper)
Nov  1 06:55:09 Devin-HP dbus[992]: [system] Successfully activated service 'org.freedesktop.hostname1'
Nov  1 06:56:15 Devin-HP sudo: pam_ecryptfs: pam_sm_authenticate: /home/devin is already mounted
Nov  1 06:56:33 Devin-HP ntfs-3g[27339]: Unmounting /dev/sdb1 (My Passport)
Nov  1 06:56:33 Devin-HP udisksd[2426]: Cleaning up mount point /media/devin/My Passport1 (device 8:17 is not mounted)
Nov  1 06:56:33 Devin-HP udisksd[2426]: Unmounted /dev/sdb1 on behalf of uid 1000
Nov  1 06:56:33 Devin-HP kernel: [561174.819414] usb 2-1.2: USB disconnect, device number 8

```

---

### Post by bab1 on 2013-11-01
> **dberg said:**
> It finally happened again. I have pasted my syslog but I don't necessarily see anything that looks to contain the fact that the folder was not deleted at any time so I'm not sure that the event was captured in the logs this time either.

```
...
Oct 31 18:12:37 Devin-HP kernel: [515358.253898] usb 1-1.5: new high-speed USB device number 7 using ehci-pci
Oct 31 18:12:37 Devin-HP kernel: [515358.361209] usb 1-1.5: New USB device found, idVendor=0bda, idProduct=0158
Oct 31 18:12:37 Devin-HP kernel: [515358.361219] usb 1-1.5: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Oct 31 18:12:37 Devin-HP kernel: [515358.361225] usb 1-1.5: Product: USB2.0-CRW
Oct 31 18:12:37 Devin-HP kernel: [515358.361229] usb 1-1.5: Manufacturer: Generic
Oct 31 18:12:37 Devin-HP kernel: [515358.361234] usb 1-1.5: SerialNumber: 20071114173400000
Oct 31 18:12:37 Devin-HP kernel: [515358.366384] ums-realtek 1-1.5:1.0: USB Mass Storage device detected
Oct 31 18:12:37 Devin-HP kernel: [515358.377421] scsi9 : usb-storage 1-1.5:1.0
Oct 31 18:12:38 Devin-HP mtp-probe: checking bus 1, device 7: "/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5"
Oct 31 18:12:38 Devin-HP mtp-probe: bus: 1, device: 7 was not an MTP device
Oct 31 18:12:38 Devin-HP kernel: [515359.379801] scsi 9:0:0:0: Direct-Access     Generic- Multi-Card       1.00 PQ: 0 ANSI: 0 CCS
Oct 31 18:12:38 Devin-HP kernel: [515359.380160] sd 9:0:0:0: Attached scsi generic sg2 type 0
Oct 31 18:12:39 Devin-HP kernel: [515360.073837] sd 9:0:0:0: [sdb] 7862272 512-byte logical blocks: (4.02 GB/3.74 GiB)
Oct 31 18:12:39 Devin-HP kernel: [515360.074753] sd 9:0:0:0: [sdb] Write Protect is off
Oct 31 18:12:39 Devin-HP kernel: [515360.074761] sd 9:0:0:0: [sdb] Mode Sense: 03 00 00 00
Oct 31 18:12:39 Devin-HP kernel: [515360.075880] sd 9:0:0:0: [sdb] No Caching mode page found
Oct 31 18:12:39 Devin-HP kernel: [515360.075887] sd 9:0:0:0: [sdb] Assuming drive cache: write through
Oct 31 18:12:39 Devin-HP kernel: [515360.079988] sd 9:0:0:0: [sdb] No Caching mode page found
Oct 31 18:12:39 Devin-HP kernel: [515360.079999] sd 9:0:0:0: [sdb] Assuming drive cache: write through
Oct 31 18:12:39 Devin-HP kernel: [515360.080974]  sdb: sdb1
Oct 31 18:12:39 Devin-HP kernel: [515360.084607] sd 9:0:0:0: [sdb] No Caching mode page found
Oct 31 18:12:39 Devin-HP kernel: [515360.084619] sd 9:0:0:0: [sdb] Assuming drive cache: write through
Oct 31 18:12:39 Devin-HP kernel: [515360.084624] sd 9:0:0:0: [sdb] Attached SCSI removable disk
Oct 31 18:12:41 Devin-HP udisksd[2426]: Mounted /dev/sdb1 at /media/devin/disk on behalf of uid 1000

...


Oct 31 18:41:37 Devin-HP udisksd[2426]: Cleaning up mount point /media/devin/disk (device 8:17 is not mounted)
Oct 31 18:41:38 Devin-HP udisksd[2426]: Unmounted /dev/sdb1 on behalf of uid 1000
Oct 31 18:41:39 Devin-HP kernel: [517099.908358] sdb: detected capacity change from 4025483264 to 0
Oct 31 18:41:41 Devin-HP kernel: [517102.078377] usb 1-1.5: USB disconnect, device number 7

...

[COLOR="#FF0000"]Oct 31 23:37:57 Devin-HP kernel: [534870.555487] CPU1: Core temperature above threshold, cpu clock throttled (total events = 1)
Oct 31 23:37:57 Devin-HP kernel: [534870.555492] CPU0: Core temperature above threshold, cpu clock throttled (total events = 1)
Oct 31 23:37:57 Devin-HP kernel: [534870.556532] CPU0: Core temperature/speed normal
Oct 31 23:37:57 Devin-HP kernel: [534870.556533] CPU1: Core temperature/speed normal
Oct 31 23:39:13 Devin-HP NetworkManager[1071]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted
Oct 31 23:39:41 Devin-HP kernel: [534974.080922] mce: [Hardware Error]: Machine check events logged
Oct 31 23:45:13 Devin-HP NetworkManager[1071]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted
Oct 31 23:47:27 Devin-HP kernel: [535440.402039] CPU1: Core temperature above threshold, cpu clock throttled (total events = 17)
Oct 31 23:47:27 Devin-HP kernel: [535440.402045] CPU0: Core temperature above threshold, cpu clock throttled (total events = 17)
Oct 31 23:47:27 Devin-HP kernel: [535440.403088] CPU0: Core temperature/speed normal
Oct 31 23:47:27 Devin-HP kernel: [535440.403089] CPU1: Core temperature/speed normal[/COLOR]
...

[COLOR="#FF0000"]Oct 31 23:51:50 Devin-HP kernel: [535702.737032] mce: [Hardware Error]: Machine check events logged
Oct 31 23:52:33 Devin-HP kernel: [535745.967882] CPU0: Core temperature above threshold, cpu clock throttled (total events = 56)
Oct 31 23:52:33 Devin-HP kernel: [535745.967884] CPU1: Core temperature above threshold, cpu clock throttled (total events = 56)
Oct 31 23:52:33 Devin-HP kernel: [535745.968933] CPU0: Core temperature/speed normal
Oct 31 23:52:33 Devin-HP kernel: [535745.968934] CPU1: Core temperature/speed normal
Oct 31 23:54:20 Devin-HP kernel: [535852.673682] mce: [Hardware Error]: Machine check events logged
Nov  1 00:01:10 Devin-HP kernel: [536262.392065] CPU0: Core temperature above threshold, cpu clock throttled (total events = 93)
Nov  1 00:01:10 Devin-HP kernel: [536262.392067] CPU1: Core temperature above threshold, cpu clock throttled (total events = 93)
Nov  1 00:01:10 Devin-HP kernel: [536262.393097] CPU1: Core temperature/speed normal
Nov  1 00:01:10 Devin-HP kernel: [536262.393098] CPU0: Core temperature/speed normal
Nov  1 00:01:50 Devin-HP kernel: [536302.495649] mce: [Hardware Error]: Machine check events logged
Nov  1 00:07:33 Devin-HP kernel: [536645.644824] CPU0: Core temperature above threshold, cpu clock throttled (total events = 96)
Nov  1 00:07:33 Devin-HP kernel: [536645.644830] CPU1: Core temperature above threshold, cpu clock throttled (total events = 96)
Nov  1 00:07:33 Devin-HP kernel: [536645.645868] CPU0: Core temperature/speed normal
Nov  1 00:07:33 Devin-HP kernel: [536645.645869] CPU1: Core temperature/speed normal
Nov  1 00:08:05 Devin-HP kernel: [536677.325263] mce: [Hardware Error]: Machine check events logged
Nov  1 00:13:45 Devin-HP kernel: [537017.019251] CPU3: Core temperature above threshold, cpu clock throttled (total events = 15)
Nov  1 00:13:45 Devin-HP kernel: [537017.019257] CPU2: Core temperature above threshold, cpu clock throttled (total events = 15)
Nov  1 00:13:45 Devin-HP kernel: [537017.020299] CPU3: Core temperature/speed normal
Nov  1 00:13:45 Devin-HP kernel: [537017.020300] CPU2: Core temperature/speed normal
Nov  1 00:14:20 Devin-HP kernel: [537052.178887] mce: [Hardware Error]: Machine check events logged
Nov  1 00:17:04 Devin-HP CRON[26472]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov  1 00:23:05 Devin-HP kernel: [537576.623202] CPU1: Core temperature above threshold, cpu clock throttled (total events = 121)
Nov  1 00:23:05 Devin-HP kernel: [537576.623208] CPU0: Core temperature above threshold, cpu clock throttled (total events = 121)
Nov  1 00:23:05 Devin-HP kernel: [537576.624247] CPU0: Core temperature/speed normal
Nov  1 00:23:05 Devin-HP kernel: [537576.624248] CPU1: Core temperature/speed normal
Nov  1 00:25:35 Devin-HP kernel: [537726.881751] mce: [Hardware Error]: Machine check events logged
Nov  1 00:32:47 Devin-HP kernel: [538159.204389] CPU0: Core temperature above threshold, cpu clock throttled (total events = 224)
Nov  1 00:32:47 Devin-HP kernel: [538159.204391] CPU1: Core temperature above threshold, cpu clock throttled (total events = 224)
Nov  1 00:32:47 Devin-HP kernel: [538159.205438] CPU1: Core temperature/speed normal
Nov  1 00:32:47 Devin-HP kernel: [538159.205439] CPU0: Core temperature/speed normal
Nov  1 00:33:05 Devin-HP kernel: [538176.691662] mce: [Hardware Error]: Machine check events logged
Nov  1 00:42:29 Devin-HP kernel: [538740.388968] CPU3: Core temperature above threshold, cpu clock throttled (total events = 172)
Nov  1 00:42:29 Devin-HP kernel: [538740.388974] CPU2: Core temperature above threshold, cpu clock throttled (total events = 172)
Nov  1 00:42:29 Devin-HP kernel: [538740.390017] CPU3: Core temperature/speed normal
Nov  1 00:42:29 Devin-HP kernel: [538740.390018] CPU2: Core temperature/speed normal
Nov  1 00:49:11 Devin-HP kernel: [539142.241328] CPU3: Core temperature above threshold, cpu clock throttled (total events = 177)
Nov  1 00:49:11 Devin-HP kernel: [539142.241330] CPU2: Core temperature above threshold, cpu clock throttled (total events = 177)
Nov  1 00:49:11 Devin-HP kernel: [539142.242373] CPU3: Core temperature/speed normal
Nov  1 00:49:11 Devin-HP kernel: [539142.242373] CPU2: Core temperature/speed normal
Nov  1 00:50:12 Devin-HP whoopsie[1382]: online
Nov  1 00:51:31  whoopsie[1382]: last message repeated 2 times
Nov  1 00:57:36 Devin-HP kernel: [539647.451889] CPU3: Core temperature above threshold, cpu clock throttled (total events = 312)
Nov  1 00:57:36 Devin-HP kernel: [539647.451894] CPU2: Core temperature above threshold, cpu clock throttled (total events = 312)
Nov  1 00:57:36 Devin-HP kernel: [539647.452939] CPU3: Core temperature/speed normal
Nov  1 00:57:36 Devin-HP kernel: [539647.452940] CPU2: Core temperature/speed normal
Nov  1 01:02:51 Devin-HP kernel: [539962.426124] CPU1: Core temperature above threshold, cpu clock throttled (total events = 514)
Nov  1 01:02:51 Devin-HP kernel: [539962.426125] CPU0: Core temperature above threshold, cpu clock throttled (total events = 514)
Nov  1 01:02:51 Devin-HP kernel: [539962.427174] CPU1: Core temperature/speed normal
Nov  1 01:02:51 Devin-HP kernel: [539962.427175] CPU0: Core temperature/speed normal
Nov  1 01:13:18 Devin-HP kernel: [540588.830002] CPU0: Core temperature above threshold, cpu clock throttled (total events = 529)
Nov  1 01:13:18 Devin-HP kernel: [540588.830004] CPU1: Core temperature above threshold, cpu clock throttled (total events = 529)
Nov  1 01:13:18 Devin-HP kernel: [540588.831053] CPU0: Core temperature/speed normal
Nov  1 01:13:18 Devin-HP kernel: [540588.831054] CPU1: Core temperature/speed normal
Nov  1 01:17:05 Devin-HP CRON[26590]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov  1 01:18:22 Devin-HP kernel: [540892.639964] CPU0: Core temperature above threshold, cpu clock throttled (total events = 546)
Nov  1 01:18:22 Devin-HP kernel: [540892.639970] CPU1: Core temperature above threshold, cpu clock throttled (total events = 546)
Nov  1 01:18:22 Devin-HP kernel: [540892.641013] CPU0: Core temperature/speed normal
Nov  1 01:18:22 Devin-HP kernel: [540892.641014] CPU1: Core temperature/speed normal
Nov  1 01:42:45 Devin-HP kernel: [542354.588986] CPU0: Core temperature above threshold, cpu clock throttled (total events = 605)
Nov  1 01:42:45 Devin-HP kernel: [542354.588987] CPU1: Core temperature above threshold, cpu clock throttled (total events = 605)
Nov  1 01:42:45 Devin-HP kernel: [542354.590036] CPU0: Core temperature/speed normal
Nov  1 01:42:45 Devin-HP kernel: [542354.590037] CPU1: Core temperature/speed normal
Nov  1 01:48:42 Devin-HP kernel: [542712.128835] CPU0: Core temperature above threshold, cpu clock throttled (total events = 614)
Nov  1 01:48:42 Devin-HP kernel: [542712.128840] CPU1: Core temperature above threshold, cpu clock throttled (total events = 614)
Nov  1 01:48:42 Devin-HP kernel: [542712.129877] CPU1: Core temperature/speed normal
Nov  1 01:48:42 Devin-HP kernel: [542712.129883] CPU0: Core temperature/speed normal
Nov  1 01:50:14 Devin-HP whoopsie[1382]: online
Nov  1 01:51:34  whoopsie[1382]: last message repeated 2 times
Nov  1 01:55:31 Devin-HP wpa_supplicant[1147]: wlan0: WPA: Group rekeying completed with [redacted] [GTK=CCMP]
Nov  1 02:07:33 Devin-HP kernel: [543842.222490] CPU1: Core temperature above threshold, cpu clock throttled (total events = 838)
Nov  1 02:07:33 Devin-HP kernel: [543842.222496] CPU0: Core temperature above threshold, cpu clock throttled (total events = 838)
Nov  1 02:07:33 Devin-HP kernel: [543842.224591] CPU1: Core temperature/speed normal
Nov  1 02:07:33 Devin-HP kernel: [543842.224592] CPU0: Core temperature/speed normal
Nov  1 02:15:55 Devin-HP kernel: [544344.320498] CPU1: Core temperature above threshold, cpu clock throttled (total events = 880)
Nov  1 02:15:55 Devin-HP kernel: [544344.320504] CPU0: Core temperature above threshold, cpu clock throttled (total events = 880)
Nov  1 02:15:55 Devin-HP kernel: [544344.321546] CPU0: Core temperature/speed normal
Nov  1 02:15:55 Devin-HP kernel: [544344.321547] CPU1: Core temperature/speed normal
Nov  1 02:17:05 Devin-HP CRON[26711]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov  1 02:19:13 Devin-HP NetworkManager[1071]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted
Nov  1 02:22:41 Devin-HP kernel: [544749.739839] CPU1: Core temperature above threshold, cpu clock throttled (total events = 899)
Nov  1 02:22:41 Devin-HP kernel: [544749.739845] CPU0: Core temperature above threshold, cpu clock throttled (total events = 899)
Nov  1 02:22:41 Devin-HP kernel: [544749.741940] CPU1: Core temperature/speed normal
Nov  1 02:22:41 Devin-HP kernel: [544749.741941] CPU0: Core temperature/speed normal
Nov  1 02:25:13 Devin-HP NetworkManager[1071]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted
Nov  1 02:28:20 Devin-HP kernel: [545089.319144] CPU0: Core temperature above threshold, cpu clock throttled (total events = 973)
Nov  1 02:28:20 Devin-HP kernel: [545089.319146] CPU1: Core temperature above threshold, cpu clock throttled (total events = 973)
Nov  1 02:28:20 Devin-HP kernel: [545089.320196] CPU1: Core temperature/speed normal
Nov  1 02:28:20 Devin-HP kernel: [545089.320197] CPU0: Core temperature/speed normal
Nov  1 02:37:08 Devin-HP kernel: [545616.392880] CPU1: Core temperature above threshold, cpu clock throttled (total events = 1064)
Nov  1 02:37:08 Devin-HP kernel: [545616.392886] CPU0: Core temperature above threshold, cpu clock throttled (total events = 1064)
Nov  1 02:37:08 Devin-HP kernel: [545616.393926] CPU1: Core temperature/speed normal
Nov  1 02:37:08 Devin-HP kernel: [545616.393927] CPU0: Core temperature/speed normal
Nov  1 02:41:13 Devin-HP NetworkManager[1071]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted
Nov  1 02:49:01 Devin-HP kernel: [546329.765397] CPU0: Core temperature above threshold, cpu clock throttled (total events = 1081)
Nov  1 02:49:01 Devin-HP kernel: [546329.765399] CPU1: Core temperature above threshold, cpu clock throttled (total events = 1081)
Nov  1 02:49:01 Devin-HP kernel: [546329.766447] CPU0: Core temperature/speed normal
Nov  1 02:49:01 Devin-HP kernel: [546329.766448] CPU1: Core temperature/speed normal
Nov  1 02:50:12 Devin-HP whoopsie[1382]: online
Nov  1 02:51:37  whoopsie[1382]: last message repeated 2 times
Nov  1 02:57:26 Devin-HP kernel: [546834.322332] CPU0: Core temperature above threshold, cpu clock throttled (total events = 1105)
Nov  1 02:57:26 Devin-HP kernel: [546834.322337] CPU1: Core temperature above threshold, cpu clock throttled (total events = 1105)
Nov  1 02:57:26 Devin-HP kernel: [546834.323379] CPU1: Core temperature/speed normal
Nov  1 02:57:26 Devin-HP kernel: [546834.323379] CPU0: Core temperature/speed normal 

Nov  1 03:59:13 Devin-HP NetworkManager[1071]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted
Nov  1 04:06:33 Devin-HP kernel: [550979.443479] CPU1: Core temperature above threshold, cpu clock throttled (total events = 1144)
Nov  1 04:06:33 Devin-HP kernel: [550979.443481] CPU0: Core temperature above threshold, cpu clock throttled (total events = 1144)
Nov  1 04:06:33 Devin-HP kernel: [550979.444531] CPU1: Core temperature/speed normal
Nov  1 04:06:33 Devin-HP kernel: [550979.444531] CPU0: Core temperature/speed normal
Nov  1 04:17:06 Devin-HP CRON[26955]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov  1 04:50:12 Devin-HP whoopsie[1382]: online
Nov  1 04:51:13  whoopsie[1382]: last message repeated 2 times
Nov  1 05:02:23 Devin-HP kernel: [554328.170081] CPU1: Core temperature above threshold, cpu clock throttled (total events = 1209)
Nov  1 05:02:23 Devin-HP kernel: [554328.170087] CPU0: Core temperature above threshold, cpu clock throttled (total events = 1209)
Nov  1 05:02:23 Devin-HP kernel: [554328.171127] CPU1: Core temperature/speed normal
Nov  1 05:02:23 Devin-HP kernel: [554328.171128] CPU0: Core temperature/speed normal[/COLOR]
...

Nov  1 06:54:34 Devin-HP kernel: [561055.784400] usb 2-1.1: new low-speed USB device number 7 using ehci-pci
Nov  1 06:54:34 Devin-HP kernel: [561055.882110] usb 2-1.1: New USB device found, idVendor=413c, idProduct=3016
Nov  1 06:54:34 Devin-HP kernel: [561055.882119] usb 2-1.1: New USB device strings: Mfr=0, Product=2, SerialNumber=0
Nov  1 06:54:34 Devin-HP kernel: [561055.882124] usb 2-1.1: Product: Dell Premium USB Optical Mouse
...

Nov  1 06:54:57 Devin-HP kernel: [561079.270287] usb 2-1.2: new high-speed USB device number 8 using ehci-pci
Nov  1 06:54:57 Devin-HP kernel: [561079.363751] usb 2-1.2: New USB device found, idVendor=1058, idProduct=0740
Nov  1 06:54:57 Devin-HP kernel: [561079.363761] usb 2-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=5
Nov  1 06:54:57 Devin-HP kernel: [561079.363767] usb 2-1.2: Product: My Passport 0740
Nov  1 06:54:57 Devin-HP kernel: [561079.363772] usb 2-1.2: Manufacturer: Western Digital
Nov  1 06:54:57 Devin-HP kernel: [561079.363776] usb 2-1.2: SerialNumber: [redacted]
Nov  1 06:54:57 Devin-HP kernel: [561079.364547] usb-storage 2-1.2:1.0: USB Mass Storage device detected
Nov  1 06:54:57 Devin-HP kernel: [561079.364723] scsi10 : usb-storage 2-1.2:1.0
Nov  1 06:54:57 Devin-HP mtp-probe: checking bus 2, device 8: "/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2"
Nov  1 06:54:57 Devin-HP mtp-probe: bus: 2, device: 8 was not an MTP device
Nov  1 06:54:58 Devin-HP kernel: [561080.362698] scsi 10:0:0:0: Direct-Access     WD       My Passport 0740 1003 PQ: 0 ANSI: 6
Nov  1 06:54:58 Devin-HP kernel: [561080.363291] scsi 10:0:0:1: Enclosure         WD       SES Device       1003 PQ: 0 ANSI: 6
Nov  1 06:54:58 Devin-HP kernel: [561080.364074] sd 10:0:0:0: Attached scsi generic sg2 type 0
Nov  1 06:54:58 Devin-HP kernel: [561080.364313] ses 10:0:0:1: Attached Enclosure device
Nov  1 06:54:58 Devin-HP kernel: [561080.364496] ses 10:0:0:1: Attached scsi generic sg3 type 13
Nov  1 06:55:04 Devin-HP kernel: [561085.927831] sd 10:0:0:0: [sdb] 1953458176 512-byte logical blocks: (1.00 TB/931 GiB)
Nov  1 06:55:04 Devin-HP kernel: [561085.929850] sd 10:0:0:0: [sdb] Write Protect is off
Nov  1 06:55:04 Devin-HP kernel: [561085.929861] sd 10:0:0:0: [sdb] Mode Sense: 47 00 10 08
Nov  1 06:55:04 Devin-HP kernel: [561085.931275] sd 10:0:0:0: [sdb] No Caching mode page found
Nov  1 06:55:04 Devin-HP kernel: [561085.931285] sd 10:0:0:0: [sdb] Assuming drive cache: write through
Nov  1 06:55:04 Devin-HP kernel: [561085.936910] sd 10:0:0:0: [sdb] No Caching mode page found
Nov  1 06:55:04 Devin-HP kernel: [561085.936920] sd 10:0:0:0: [sdb] Assuming drive cache: write through
Nov  1 06:55:04 Devin-HP kernel: [561085.948670]  sdb: sdb1
Nov  1 06:55:04 Devin-HP kernel: [561085.952150] sd 10:0:0:0: [sdb] No Caching mode page found
Nov  1 06:55:04 Devin-HP kernel: [561085.952159] sd 10:0:0:0: [sdb] Assuming drive cache: write through
Nov  1 06:55:04 Devin-HP kernel: [561085.952165] sd 10:0:0:0: [sdb] Attached SCSI disk
Nov  1 06:55:07 Devin-HP ntfs-3g[27339]: Version 2013.1.13AR.1 external FUSE 29
Nov  1 06:55:07 Devin-HP ntfs-3g[27339]: Mounted /dev/sdb1 (Read-Write, label "My Passport", NTFS 3.1)
Nov  1 06:55:07 Devin-HP ntfs-3g[27339]: Cmdline options: rw,nosuid,nodev,uhelper=udisks2,uid=1000,gid=1000,dmask=0077,fmask=0177
Nov  1 06:55:07 Devin-HP ntfs-3g[27339]: Mount options: rw,nosuid,nodev,uhelper=udisks2,allow_other,nonempty,relatime,default_permissions,fsname=/dev/sdb1,blkdev,blksize=4096
Nov  1 06:55:07 Devin-HP ntfs-3g[27339]: Global ownership and permissions enforced, configuration type 7
Nov  1 06:55:07 Devin-HP udisksd[2426]: Mounted /dev/sdb1 at /media/devin/My Passport1 on behalf of uid 1000
Nov  1 06:55:09 Devin-HP dbus[992]: [system] Activating service name='org.freedesktop.hostname1' (using servicehelper)
Nov  1 06:55:09 Devin-HP dbus[992]: [system] Successfully activated service 'org.freedesktop.hostname1'
Nov  1 06:56:15 Devin-HP sudo: pam_ecryptfs: pam_sm_authenticate: /home/devin is already mounted
Nov  1 06:56:33 Devin-HP ntfs-3g[27339]: Unmounting /dev/sdb1 (My Passport)
Nov  1 06:56:33 Devin-HP udisksd[2426]: Cleaning up mount point /media/devin/My Passport1 (device 8:17 is not mounted)
Nov  1 06:56:33 Devin-HP udisksd[2426]: Unmounted /dev/sdb1 on behalf of uid 1000
Nov  1 06:56:33 Devin-HP kernel: [561174.819414] usb 2-1.2: USB disconnect, device number 8

```

There doesn't seem to be anything abnormal with the mounts.  It does appear that you are mounting 2 different devices (at different times) as /dev/sdb1.  Hopefully Crashplan knows the differences between them.

I notice that the CPU is running very hot.  That is something you need to look into.

At this point I thing your best bet is to deal with Crashplan.  Both the USB stick and the Passport seem to be dismounted cleanly.

---

