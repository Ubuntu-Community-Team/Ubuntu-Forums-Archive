---
title: "Suddenly unable to write to external hard drive, can't change permissions"
date: 2008-04-27
forum: General Help
---

### Post by Seseli on 2008-04-27
My mp3-player, which is an iRiver IFP-799 and works just as an external hard drive when I connect it to the computer, suddenly refuses to let me copy files to it. When I check the permissions, it turns out that my user, which is the owner of the device, does not have any file access. When I try to change the file access to "read and write", it just doesn't react to that. It worked fine earlier today. 

I'm running Ubuntu 7.10.

Grateful for help. : )

---

### Post by ghost_ryder35 on 2008-04-27
I think the problem is that it is mounted with wrong permissions, so maybe you can unmount it and change the permissions then remount it.  This page has some useful information and links at the bottom of the page [[COLOR=#444444]http://psychocats.net/ubuntu/mountlinux[/COLOR]]("http://psychocats.net/ubuntu/mountlinux")

---

### Post by Seseli on 2008-04-27
Okay, I tried to follow the suggestions there. I looked at the drive in GParted, where it said that it had file system fat16. Then I created a mount point for it and edited fstab, but when I typed in 

sudo mount -a

it complained that fat16 was an unknown filesystem...

---

### Post by ghost_ryder35 on 2008-04-27
can you try that again and post the error message it gave you

---

### Post by Seseli on 2008-04-27
It says: 

mount: unknown filesystem type 'fat16'
mount: maybe you meant 'vfat'?

---

### Post by ghost_ryder35 on 2008-04-27
yea change it to vfat and see what happens :).  I think that since fat16 is so old that it is not supportated anymore and they only use vfat now... maybe I'm wrong though :(

---

### Post by Seseli on 2008-04-27
All right, now it's mounted! 

But when I run

gksudo nautilus

and then try to change the ownership of the disk from root to my user, it says that it can't, because it's a read-only disk? And neither can I change it to "read and write files" for the root user.

---

### Post by chrisccoulson on 2008-04-27
For an external disk like this, you shouldn't really need to add a line in your fstab to mount it. It should automount correctly and you should be able to write to it (as long as you're a member of the plugdev group).

Because it used to work and has suddenly stopped working, this sounds like the classic symptoms of filesystem errors, and no amount of changing mount options will fix it. You will probably need to run dosfsck on it to fix. This is a common problem with FAT volumes, and normally occurs after is was uncleanly unmounted (pulling the cable out / power failure / crash etc)

With the line removed from your fstab, please plug in the drive and let it auto-mount, then have a look for errors in your /var/log/syslog:
```
tail -n 20 /var/log/syslog
```

---

### Post by Seseli on 2008-04-27
Hmm, will running the dosfsck thing affect the way it works as an mp3 player? I mean, I guess there are programs running in it to play the music...

Anyway. This is what I get when I run

tail -n 20 /var/log/syslog

Apr 27 17:51:08 tuktoyaktuk NetworkManager: <debug> [1209311468.607711] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_iriver_MassStorage_Disc_0_0'). 
Apr 27 17:51:08 tuktoyaktuk NetworkManager: <debug> [1209311468.660548] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_20E6_A088'). 
Apr 27 17:51:08 tuktoyaktuk hald: mounted /dev/sdg on behalf of uid 1000
Apr 27 17:51:08 tuktoyaktuk kernel: [ 2670.213737] FAT: Filesystem panic (dev sdg)
Apr 27 17:51:08 tuktoyaktuk kernel: [ 2670.213743]     fat_get_cluster: invalid cluster chain (i_pos 0)
Apr 27 17:51:08 tuktoyaktuk kernel: [ 2670.213747]     File system has been set read-only
Apr 27 17:51:08 tuktoyaktuk kernel: [ 2670.214730] FAT: Filesystem panic (dev sdg)
Apr 27 17:51:08 tuktoyaktuk kernel: [ 2670.214735]     fat_get_cluster: invalid cluster chain (i_pos 0)
Apr 27 17:51:08 tuktoyaktuk kernel: [ 2670.221820] FAT: Filesystem panic (dev sdg)
Apr 27 17:51:08 tuktoyaktuk kernel: [ 2670.221828]     fat_get_cluster: invalid cluster chain (i_pos 0)
Apr 27 17:51:08 tuktoyaktuk kernel: [ 2670.222012] FAT: Filesystem panic (dev sdg)
Apr 27 17:51:08 tuktoyaktuk kernel: [ 2670.222014]     fat_get_cluster: invalid cluster chain (i_pos 0)
Apr 27 17:51:11 tuktoyaktuk kernel: [ 2672.537451] FAT: Filesystem panic (dev sdg)
Apr 27 17:51:11 tuktoyaktuk kernel: [ 2672.537459]     fat_get_cluster: invalid cluster chain (i_pos 0)
Apr 27 17:51:11 tuktoyaktuk kernel: [ 2672.545624] FAT: Filesystem panic (dev sdg)
Apr 27 17:51:11 tuktoyaktuk kernel: [ 2672.545632]     fat_get_cluster: invalid cluster chain (i_pos 0)
Apr 27 17:51:11 tuktoyaktuk kernel: [ 2672.547869] FAT: Filesystem panic (dev sdg)
Apr 27 17:51:11 tuktoyaktuk kernel: [ 2672.547875]     fat_get_cluster: invalid cluster chain (i_pos 0)
Apr 27 17:51:11 tuktoyaktuk kernel: [ 2672.556347] FAT: Filesystem panic (dev sdg)
Apr 27 17:51:11 tuktoyaktuk kernel: [ 2672.556356]     fat_get_cluster: invalid cluster chain (i_pos 0)

---

### Post by chrisccoulson on 2008-04-27
As suspected, you've got filesystem errors. You need to unmount the volume and then run dosfsck to fix:
```
sudo umount /dev/sdxx
sudo dosfsck -av /dev/sdxx
```
where /dev/sdxx is the device node for your iRiver.

Fixing the filesystem shouldn't affect your iRiver. AFAIK, it just uses the disk for storage, and will rely on a good filesystem to work reliably anyway.

---

### Post by Seseli on 2008-04-27
Yay, it worked!

Thank you so much, both of you, for taking the time to help me out. 
: )

---

### Post by Wilden on 2008-05-26
> **chrisccoulson said:**
> 
```
sudo umount /dev/sdxx
sudo dosfsck -av /dev/sdxx
```


Would doing this affect the files on such a file system? I have the same problem but the drive in question is where I store all my files and unfortunately I have no-where to back them up.

---

### Post by chrisccoulson on 2008-05-26
> **Wilden said:**
> Would doing this affect the files on such a file system? I have the same problem but the drive in question is where I store all my files and unfortunately I have no-where to back them up.

Is the filesystem actually broken? Please monitor the output of 'tail -f /var/log/syslog' as you plug the drive in.

If the filesystem is broken, then you have no option but to run dosfsck on it. I can't say that some of your files won't be broken already

---

### Post by Wilden on 2008-05-26
> May 26 12:01:59 wilden-eee kernel: [ 4026.324000] usb 5-3: new high speed USB device using ehci_hcd and address 8
May 26 12:01:59 wilden-eee NetworkManager: <debug> [1211799719.777174] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_d49_3200_2CAH210F'). 
May 26 12:01:59 wilden-eee kernel: [ 4026.472000] usb 5-3: configuration #1 chosen from 1 choice
May 26 12:01:59 wilden-eee kernel: [ 4026.472000] scsi6 : SCSI emulation for USB Mass Storage devices
May 26 12:01:59 wilden-eee kernel: [ 4026.472000] usb-storage: device found at 8
May 26 12:01:59 wilden-eee kernel: [ 4026.472000] usb-storage: waiting for device to settle before scanning
May 26 12:02:00 wilden-eee NetworkManager: <debug> [1211799720.024280] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_d49_3200_2CAH210F_if0'). 
May 26 12:02:00 wilden-eee NetworkManager: <debug> [1211799720.117132] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_d49_3200_2CAH210F_usbraw'). 
May 26 12:02:04 wilden-eee kernel: [ 4031.472000] usb-storage: device scan complete
May 26 12:02:05 wilden-eee kernel: [ 4032.212000] scsi 6:0:0:0: Direct-Access     Maxtor   3200             0344 PQ: 0 ANSI: 4
May 26 12:02:05 wilden-eee kernel: [ 4032.216000] sd 6:0:0:0: [sdc] 625142448 512-byte hardware sectors (320073 MB)
May 26 12:02:05 wilden-eee kernel: [ 4032.216000] sd 6:0:0:0: [sdc] Write Protect is off
May 26 12:02:05 wilden-eee kernel: [ 4032.216000] sd 6:0:0:0: [sdc] Mode Sense: 17 00 00 00
May 26 12:02:05 wilden-eee kernel: [ 4032.216000] sd 6:0:0:0: [sdc] Assuming drive cache: write through
May 26 12:02:05 wilden-eee kernel: [ 4032.216000] sd 6:0:0:0: [sdc] 625142448 512-byte hardware sectors (320073 MB)
May 26 12:02:05 wilden-eee kernel: [ 4032.216000] sd 6:0:0:0: [sdc] Write Protect is off
May 26 12:02:05 wilden-eee kernel: [ 4032.216000] sd 6:0:0:0: [sdc] Mode Sense: 17 00 00 00
May 26 12:02:05 wilden-eee kernel: [ 4032.216000] sd 6:0:0:0: [sdc] Assuming drive cache: write through
May 26 12:02:05 wilden-eee kernel: [ 4032.216000]  sdc: sdc1
May 26 12:02:05 wilden-eee kernel: [ 4032.236000] sd 6:0:0:0: [sdc] Attached SCSI disk
May 26 12:02:05 wilden-eee kernel: [ 4032.236000] sd 6:0:0:0: Attached scsi generic sg2 type 0
May 26 12:02:05 wilden-eee NetworkManager: <debug> [1211799725.725172] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_d49_3200_2CAH210F_if0_scsi_host'). 
May 26 12:02:05 wilden-eee NetworkManager: <debug> [1211799725.746025] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_d49_3200_2CAH210F_if0_scsi_host_scsi_device_lun0'). 
May 26 12:02:05 wilden-eee NetworkManager: <debug> [1211799725.755353] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_d49_3200_2CAH210F_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
May 26 12:02:06 wilden-eee NetworkManager: <debug> [1211799726.055781] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_Maxtor_3200_2CAH210F_0_0'). 
May 26 12:02:06 wilden-eee NetworkManager: <debug> [1211799726.176806] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_46E7_BB4F'). 
May 26 12:02:06 wilden-eee hald: mounted /dev/sdc1 on behalf of uid 1000


It seems to be behaving itself now, though if you could shed some light on it it would be very useful.

EDIT: Nope, its doing it again, stupid thing. It just decides that its going to be read only about 10-20 mins after its mounted. This may have something to do with Bittorrent, the error messages always seem to some up in it. Plus, it says its owned by root but wont let me change this.

---

