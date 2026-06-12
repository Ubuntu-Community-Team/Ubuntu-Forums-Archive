---
title: "Installing an External Hard Drive"
date: 2008-04-28
forum: General Help
---

### Post by nigel_salvador on 2008-04-28
Here is my situation:

I recently purchased a SATA 200GB internal hard drive and connected it to a hard drive enclosure so that I would have a 200GB external hard drive. After connecting it to my computer, which is running Ubuntu Linux 7.10 it does not recognize the new external hard drive. Please help!!!

---

### Post by pholden on 2008-04-28
Have you formatted and mounted the new drive?

Here's a handy guide: [http://wiki.linuxquestions.org/wiki/Add_a_new_hard_drive](http://wiki.linuxquestions.org/wiki/Add_a_new_hard_drive) 8)

---

### Post by nigel_salvador on 2008-04-28
Thanks, I'll take a look at the link and see if that helps

---

### Post by nigel_salvador on 2008-04-28
I looked into the link that was sent and nothing. After plugging in the external hard drive Linux does not recognize it and does not supply a mount point after typing in 'mount' at the prompt. Therefore trying to use 'fdisk' proves difficult

---

### Post by martyssweb07 on 2008-04-28
I would suggest opening a terminal window, then unplug your usb HD, then in the terminal type 
tail -f /var/log/syslog
then reconnect your usb drive.
you should see something come through on your terminal. copy it and paste it into the thread here.

---

### Post by nigel_salvador on 2008-04-28
Thanks, I will try when next I'm home but can you explain what this is doing?

---

### Post by martyssweb07 on 2008-04-28
sure the syslog logs quite a bit of system activity, one such thing it logs is hardware changes.  if you do a tail is list the last few lines of a file, if you do a tail -f is list the last few lines a file but keeps the connection open, so any appends to the file show up on your terminal in real time.

hence when you plug in your usb drive, it should show the connection and what it's doing.  in alot of cases with hardy in particular, it actually is detecting the hardware and doing "something with it" but not necessarily what you want.  So, if it is in fact detecting it, and loading the proper kernel modules, the syslog will show that.  and then it's probably just a mounting issue. other wise, it might be there is some kernel module which might need to be loaded.  

Hopefully if you post the output, well be able to figure which it is, and get it going.  it could be also that it's just not mounting it in a place you recognize.  ie my SD card mounts to /dev/mmcblk0p1 why, beats me but if i add
/dev/mmcblk0p1 /media/SD vfat nosuid,auto,nodev,rw,umask=077,gid=1000,uid=1000,user,defaults,noatime,iocharset=utf8 0 0 
to my fstab bingo.

Hope this explained abit.

---

### Post by nigel_salvador on 2008-04-28
Here is the result of your suggestion, I believe that it worked, but I do not know what it is I'm looking at:



nigelsalvador@nigelsalvador-desktop:~$ tail -f /var/log/syslog
Apr 28 16:17:01 nigelsalvador-desktop /USR/SBIN/CRON[9754]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 28 16:46:50 nigelsalvador-desktop -- MARK --
Apr 28 16:56:15 nigelsalvador-desktop NetworkManager: <debug> [1209416175.860235] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4fc_c25_ST3200820A____________9QE4BF4J_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Apr 28 16:56:15 nigelsalvador-desktop kernel: [173382.824000] usb 2-3: USB disconnect, address 12
Apr 28 16:56:15 nigelsalvador-desktop NetworkManager: <debug> [1209416175.863382] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/storage_serial_ST320082_0AS_ST3200820A_9QE4BF4J_0_0'). 
Apr 28 16:56:15 nigelsalvador-desktop NetworkManager: <debug> [1209416175.864450] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4fc_c25_ST3200820A____________9QE4BF4J_if0_scsi_host_scsi_device_lun0'). 
Apr 28 16:56:15 nigelsalvador-desktop NetworkManager: <debug> [1209416175.866156] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4fc_c25_ST3200820A____________9QE4BF4J_if0_scsi_host'). 
Apr 28 16:56:15 nigelsalvador-desktop NetworkManager: <debug> [1209416175.867779] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4fc_c25_ST3200820A____________9QE4BF4J_if0'). 
Apr 28 16:56:15 nigelsalvador-desktop NetworkManager: <debug> [1209416175.869246] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4fc_c25_ST3200820A____________9QE4BF4J'). 
Apr 28 16:56:15 nigelsalvador-desktop NetworkManager: <debug> [1209416175.869304] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4fc_c25_ST3200820A____________9QE4BF4J_usbraw'). 
Apr 28 16:59:53 nigelsalvador-desktop kernel: [173600.932000] usb 2-3: new high speed USB device using ehci_hcd and address 13
Apr 28 16:59:54 nigelsalvador-desktop kernel: [173601.064000] usb 2-3: configuration #1 chosen from 1 choice
Apr 28 16:59:54 nigelsalvador-desktop kernel: [173601.068000] scsi14 : SCSI emulation for USB Mass Storage devices
Apr 28 16:59:54 nigelsalvador-desktop kernel: [173601.068000] usb-storage: device found at 13
Apr 28 16:59:54 nigelsalvador-desktop kernel: [173601.068000] usb-storage: waiting for device to settle before scanning
Apr 28 16:59:54 nigelsalvador-desktop NetworkManager: <debug> [1209416394.097812] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4fc_c25_ST3200820A____________9QE4BF4J'). 
Apr 28 16:59:54 nigelsalvador-desktop NetworkManager: <debug> [1209416394.148120] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4fc_c25_ST3200820A____________9QE4BF4J_if0'). 
Apr 28 16:59:54 nigelsalvador-desktop NetworkManager: <debug> [1209416394.164494] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4fc_c25_ST3200820A____________9QE4BF4J_usbraw'). 
Apr 28 16:59:59 nigelsalvador-desktop kernel: [173606.068000] usb-storage: device scan complete
Apr 28 16:59:59 nigelsalvador-desktop kernel: [173606.072000] scsi 14:0:0:0: Direct-Access     ST320082 0AS                   PQ: 0 ANSI: 2
Apr 28 16:59:59 nigelsalvador-desktop kernel: [173606.072000] sd 14:0:0:0: [sdb] 390721968 512-byte hardware sectors (200050 MB)
Apr 28 16:59:59 nigelsalvador-desktop kernel: [173606.076000] sd 14:0:0:0: [sdb] Write Protect is off
Apr 28 16:59:59 nigelsalvador-desktop kernel: [173606.076000] sd 14:0:0:0: [sdb] Mode Sense: 38 00 00 00
Apr 28 16:59:59 nigelsalvador-desktop kernel: [173606.076000] sd 14:0:0:0: [sdb] Assuming drive cache: write through
Apr 28 16:59:59 nigelsalvador-desktop kernel: [173606.080000] sd 14:0:0:0: [sdb] 390721968 512-byte hardware sectors (200050 MB)
Apr 28 16:59:59 nigelsalvador-desktop kernel: [173606.080000] sd 14:0:0:0: [sdb] Write Protect is off
Apr 28 16:59:59 nigelsalvador-desktop kernel: [173606.080000] sd 14:0:0:0: [sdb] Mode Sense: 38 00 00 00
Apr 28 16:59:59 nigelsalvador-desktop kernel: [173606.080000] sd 14:0:0:0: [sdb] Assuming drive cache: write through
Apr 28 17:00:02 nigelsalvador-desktop NetworkManager: <debug> [1209416402.134569] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4fc_c25_ST3200820A____________9QE4BF4J_if0_scsi_host'). 
Apr 28 17:00:02 nigelsalvador-desktop NetworkManager: <debug> [1209416402.137826] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4fc_c25_ST3200820A____________9QE4BF4J_if0_scsi_host_scsi_device_lun0'). 
Apr 28 17:00:04 nigelsalvador-desktop NetworkManager: <debug> [1209416404.225197] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4fc_c25_ST3200820A____________9QE4BF4J_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Apr 28 17:00:04 nigelsalvador-desktop kernel: [173606.080000]  sdb: unknown partition table
Apr 28 17:00:04 nigelsalvador-desktop kernel: [173611.192000] sd 14:0:0:0: [sdb] Attached SCSI disk
Apr 28 17:00:04 nigelsalvador-desktop kernel: [173611.192000] sd 14:0:0:0: Attached scsi generic sg1 type 0

---

### Post by martyssweb07 on 2008-04-28
it says it doesn't know what kind of partition it is on sdb.  
First double check, and make sure sdb or sdb1 (or any iteration thereof) is not mounted
by doing
df -h
nothing returned should say sdb(anything).
if the above is true you need to do sudo fdisk -l /dev/sdb and see what it returns. if it returns nothing for partitions which is what I'm guessing then create a partition in fdisk (let me know if you need help doing this). 
then format the filesystem 
mkfs -t ext3 /dev/sdb1
then add a place to mount it 
sudo mkdir /media/sdb1
sudo chmod -R 777 /media/sdb1
sudo chown -R your_username:your_username /media/sdb1
after that i would add a line like 
/dev/sdb1      /media/sdb1     ext3   defaults,user,rw 0 0
to your /etc/fstab

---

### Post by nigel_salvador on 2008-04-28
Actually I do need help creating a partition using fdisk, however couldn't I also use GParted to create a partition

---

### Post by nigel_salvador on 2008-04-30
Nevermind, I used GParted instead - a lot easier

---

