---
title: "[SOLVED] Cannot mound external hd"
date: 2008-02-11
forum: General Help
---

### Post by phil90 on 2008-02-11
Hello 


When I try to mount my External Hard Drive and it won't mount I keep getting the error message. (Error message posted as a screen capture) I tried many thing like Testdrive and Fsck and e2fsck and it doesn work as the disk would need to mount for those option to work. I researched on the forum and could not find anything that work.


Message: Mount:  Wrong Fs type, bad option , bad superblock  on dev/sdc1 , missing  codepage or helper program ,  or other error  In some case  useful info is found in  syslog -try  dmesg  tail   or so


How can I mount my hard drive or at least save my date and reformat it?



Thanks 




[[IMG]http://img145.imageshack.us/img145/6907/screenshotgnomemountvz5.th.png[/IMG]]("[URL=http://img145.imageshack.us/my.php?image=screenshotgnomemountvz5.png)"][[IMG]http://img145.imageshack.us/img145/6907/screenshotgnomemountvz5.th.png[/IMG]](http://img145.imageshack.us/my.php?image=screenshotgnomemountvz5.png)[/URL]

---

### Post by taurus on 2008-02-11
What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by thefatmoop on 2008-02-11
If the harddrive is using NTFS and you plugged it into a windows computer, the windows machine marks the NTFS partition as "active" or "in use", since the windows machine uses, and leaves, a cache on the computer for the ability to just unplug it without unmounting or anything. 

To fix this plug the external into a windows xp/vista machine w/e ur using and go to "safely remove hardware" and safely eject the drive. it should tell you when it's safe to remove. This will put the partition into a closed session and linux should be able to mount it. 

(if you format the external in fat32 you shouldnt have the problem, at least i've never had a problem with this with my fat32 flash drives. remember that fat32 doesn't support individual files over 4 gigs i think) 
from what i've found that works and someone correct me if i'm wrong.

---

### Post by apetresc on 2008-02-11
You may also just be using the wrong FS type. What is the contents of your /etc/fstab? Does the type match what you know the drive to be formatted as?

Also, try doing a ```
dmesg -tail
``` right after a failed mount attempt. It should spell out the problem for you.

---

### Post by phil90 on 2008-02-11
> **taurus said:**
> What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```




Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        5896        7296    11253532+   7  HPFS/NTFS
/dev/sda2               1        5707    45841446   83  Linux
/dev/sda3            5708        5895     1510110    5  Extended
/dev/sda5            5708        5895     1510078+  82  Linux swap / Solaris

Partition table entries are not in disk order



Thanks for your quick reply

Basically the hard drive is connected I got the error message and that's what this command give me.

---

### Post by phil90 on 2008-02-11
> **thefatmoop said:**
> If the harddrive is using NTFS and you plugged it into a windows computer, the windows machine marks the NTFS partition as "active" or "in use", since the windows machine uses, and leaves, a cache on the computer for the ability to just unplug it without unmounting or anything. 

To fix this plug the external into a windows xp/vista machine w/e ur using and go to "safely remove hardware" and safely eject the drive. it should tell you when it's safe to remove. This will put the partition into a closed session and linux should be able to mount it. 

(if you format the external in fat32 you shouldnt have the problem, at least i've never had a problem with this with my fat32 flash drives. remember that fat32 doesn't support individual files over 4 gigs i think) 
from what i've found that works and someone correct me if i'm wrong.



Thank you for your help. I had forgottem to mention my hard drive is EXT3

---

### Post by taurus on 2008-02-11
Are you sure it's connected and powered on because it doesn't show up at all?

```
dmesg | tail
```

---

### Post by phil90 on 2008-02-11
> **taurus said:**
> Are you sure it's connected and powered on because it doesn't show up at all?

```
dmesg | tail
```

Thanks for all your reply. yes it is powered and the error message appeared and I verified it stays on. The hard drive does not appear in FSTAB after being powered.

and for DMEsg tail


[  145.663854] usb 5-7: new high speed USB device using ehci_hcd and address 2
[  145.776380] usb 5-7: device descriptor read/64, error -71
[  145.993233] usb 5-7: device descriptor read/64, error -71
[  146.209633] usb 5-7: new high speed USB device using ehci_hcd and address 3
[  146.322226] usb 5-7: device descriptor read/64, error -71
[  146.539293] usb 5-7: device descriptor read/64, error -71
[  146.752251] usb 5-7: new high speed USB device using ehci_hcd and address 4
[  147.162178] usb 5-7: device not accepting address 4, error -71
[  147.274939] usb 5-7: new high speed USB device using ehci_hcd and address 5
[  147.681043] usb 5-7: device not accepting address 5, error -71
[  156.257091] eth1: no IPv6 routers present
[  248.799513] usb 5-7: new high speed USB device using ehci_hcd and address 6
[  248.934713] usb 5-7: configuration #1 chosen from 1 choice
[  249.078099] usbcore: registered new interface driver libusual
[  249.107125] Initializing USB Mass Storage driver...
[  249.107217] scsi2 : SCSI emulation for USB Mass Storage devices
[  249.107294] usbcore: registered new interface driver usb-storage
[  249.107298] USB Mass Storage support registered.
[  249.107426] usb-storage: device found at 6
[  249.107430] usb-storage: waiting for device to settle before scanning
[  254.104525] usb-storage: device scan complete
[  254.139881] scsi 2:0:0:0: Direct-Access     ST332062 0A               3.AA PQ: 0 ANSI: 0
[  254.141109] SCSI device sdb: 625142447 512-byte hdwr sectors (320073 MB)
[  254.141980] sdb: Write Protect is off
[  254.141983] sdb: Mode Sense: 03 00 00 00
[  254.141985] sdb: assuming drive cache: write through
[  254.142853] SCSI device sdb: 625142447 512-byte hdwr sectors (320073 MB)
[  254.143728] sdb: Write Protect is off
[  254.143731] sdb: Mode Sense: 03 00 00 00
[  254.143733] sdb: assuming drive cache: write through
[  254.143736]  sdb: sdb1
[  254.162063] sd 2:0:0:0: Attached scsi disk sdb
[  254.162125] sd 2:0:0:0: Attached scsi generic sg2 type 0
[  284.609307] usb 5-7: reset high speed USB device using ehci_hcd and address 6
[  314.843881] usb 5-7: reset high speed USB device using ehci_hcd and address 6
[  315.955762] usb 5-7: device descriptor read/64, error -71
[  316.172158] usb 5-7: device descriptor read/64, error -71
[  316.388643] usb 5-7: reset high speed USB device using ehci_hcd and address 6
[  316.501122] usb 5-7: device descriptor read/64, error -71
[  316.718118] usb 5-7: device descriptor read/64, error -71
[  316.935048] usb 5-7: reset high speed USB device using ehci_hcd and address 6
[  317.344889] usb 5-7: device not accepting address 6, error -71
[  317.457572] usb 5-7: reset high speed USB device using ehci_hcd and address 6
[  317.863447] usb 5-7: device not accepting address 6, error -71
[  317.863477] usb 5-7: USB disconnect, address 6
[  317.863754] sd 2:0:0:0: scsi: Device offlined - not ready after error recovery
[  317.863781] sd 2:0:0:0: SCSI error: return code = 0x00010000
[  317.863785] end_request: I/O error, dev sdb, sector 14399
[  317.863818] sd 2:0:0:0: SCSI error: return code = 0x00010000
[  317.863821] end_request: I/O error, dev sdb, sector 14407
[  317.863851] JBD: Failed to read block at offset 227
[  317.863860] JBD: recovery failed
[  317.863863] EXT3-fs: error loading journal.
[  317.863891] Buffer I/O error on device sdb1, logical block 1564
[  317.863897] lost page write due to I/O error on sdb1
[  317.975403] usb 5-7: new high speed USB device using ehci_hcd and address 7
[  318.087584] usb 5-7: device descriptor read/64, error -71
[  318.304599] usb 5-7: device descriptor read/64, error -71
[  318.521929] usb 5-7: new high speed USB device using ehci_hcd and address 8
[  318.638467] usb 5-7: device descriptor read/64, error -71
[  318.855493] usb 5-7: device descriptor read/64, error -71
[  319.072639] usb 5-7: new high speed USB device using ehci_hcd and address 9
[  319.480201] usb 5-7: device not accepting address 9, error -71
[  319.593113] usb 5-7: new high speed USB device using ehci_hcd and address 10
[  320.000509] usb 5-7: device not accepting address 10, error -71

---

### Post by taurus on 2008-02-11
So now it's /dev/sdb1 while the screenshot in your original message was /dev/sdc1!  Does gparted in System -> Administration (if you don't have it, install it) even detect it?

---

### Post by phil90 on 2008-02-11
> **taurus said:**
> So now it's /dev/sdb1 while the screenshot in your original message was /dev/sdc1!  Does gparted in System -> Administration (if you don't have it, install it) even detect it?

It's because when I took the screenshot I had tried on another computer to see if it woud work. I had not notice that it made a differene in the path.

No Gparted does not see it. It seem like nothing can see it.



Edit: after hours of trying everything that I could think of or find on internet I have finally been able to see the hard drive in Gparted and after a few tries after that I have been able to mount it. It  seem like I have lost everything that was on it. Now I might have to look if I can recover some stuff but I doubt so as the journal was corrupted and everything has been destroyed while trying mount it as nothing would make the disk mount and to make any changes to it I needed the system to at least see that it was there even if it would not mount.

---

### Post by taurus on 2008-02-11
Remember the last time you used it, did you just unplug it or did you actually unmounted it first before you unplugged it?

---

### Post by phil90 on 2008-02-11
> **taurus said:**
> Remember the last time you used it, did you just unplug it or did you actually unmounted it first before you unplugged it?

 now that I think about it.  it might be the reason why it does not work. Unfortunately last time I use it there was cords that were stuck so I  unplugged it unsafely by mistake and the computer told me that a drive was unsafely removed




Edit: after hours of trying out stuff I have finally been able to get the computer recognize the hard drive was connected and then get it to mount but it seem like everything was destroyed in the process I will take a look later when I have access to the hard drive and try to recover some files if I can

Thank you all for your help.

---

