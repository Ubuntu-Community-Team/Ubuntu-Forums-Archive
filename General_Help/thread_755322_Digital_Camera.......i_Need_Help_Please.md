---
title: "Digital Camera.......i Need Help Please"
date: 2008-04-14
forum: General Help
---

### Post by jeffsa12 on 2008-04-14
I have an old Samsung Digimax 130 camera. It connects through USB. Windows reads it as a mass storage device as soom as it's plugged in without the need for drivers, etc.

How do I get Nautilus to show it as if its a thumb drive? I'm running Ubuntu 7.10 with a Vbox WinXP and after screwing around a bit, I was able to get Win Explorer to read via USB.....but not Ubuntu!!!

It seems its something simple if virtual WinXP will read it through Ubuntu.
How to mount...unmount.... In a terminal?

Can I install code in fstab to auto mount, showing in Nautilus, then unmount using GUI?

What code would I insert?

Below is some code I generated from a terminal that may help.



jeff@jeff-new-dsktp:~$ tail -f /var/log/messages
Apr 14 14:10:33 jeff-new-dsktp kernel: [ 9637.591913] sd 8:0:0:0: [sde] READ CAPACITY failed
Apr 14 14:10:33 jeff-new-dsktp kernel: [ 9637.591920] sd 8:0:0:0: [sde] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
Apr 14 14:10:33 jeff-new-dsktp kernel: [ 9637.591926] sd 8:0:0:0: [sde] Sense not available.
Apr 14 14:10:33 jeff-new-dsktp kernel: [ 9637.592798] sd 8:0:0:0: [sde] Write Protect is off
Apr 14 14:10:33 jeff-new-dsktp kernel: [ 9637.592909] sd 8:0:0:0: [sde] READ CAPACITY failed
Apr 14 14:10:33 jeff-new-dsktp kernel: [ 9637.592914] sd 8:0:0:0: [sde] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
Apr 14 14:10:33 jeff-new-dsktp kernel: [ 9637.592920] sd 8:0:0:0: [sde] Sense not available.
Apr 14 14:10:33 jeff-new-dsktp kernel: [ 9637.592936] sd 8:0:0:0: [sde] Write Protect is off
Apr 14 14:10:33 jeff-new-dsktp kernel: [ 9637.593011] sd 8:0:0:0: [sde] Attached SCSI removable disk
Apr 14 14:10:33 jeff-new-dsktp kernel: [ 9637.593082] sd 8:0:0:0: Attached scsi generic sg4 type 0
Apr 14 14:11:02 jeff-new-dsktp kernel: [ 9666.279157] usb 1-2: new full speed USB device using ohci_hcd and address 6
Apr 14 14:11:02 jeff-new-dsktp kernel: [ 9666.488136] usb 1-2: configuration #1 chosen from 1 choice
Apr 14 14:11:02 jeff-new-dsktp kernel: [ 9666.490163] scsi9 : SCSI emulation for USB Mass Storage devices
Apr 14 14:11:07 jeff-new-dsktp kernel: [ 9671.492327] scsi 9:0:0:0: Direct-Access     SAMSUNG  DIGIMAX 130      1.33 PQ: 0 ANSI: 0 CCS
Apr 14 14:11:07 jeff-new-dsktp kernel: [ 9671.502291] sd 9:0:0:0: [sde] 15600 512-byte hardware sectors (8 MB)
Apr 14 14:11:37 jeff-new-dsktp kernel: [ 9701.647690] usb 1-2: reset full speed USB device using ohci_hcd and address 6
Apr 14 14:12:07 jeff-new-dsktp kernel: [ 9731.997272] usb 1-2: reset full speed USB device using ohci_hcd and address 6
Apr 14 14:12:38 jeff-new-dsktp kernel: [ 9762.334863] usb 1-2: reset full speed USB device using ohci_hcd and address 6
Apr 14 14:13:08 jeff-new-dsktp kernel: [ 9792.688427] usb 1-2: reset full speed USB device using ohci_hcd and address 6
Apr 14 14:13:39 jeff-new-dsktp kernel: [ 9823.038017] usb 1-2: reset full speed USB device using ohci_hcd and address 6
Apr 14 14:14:09 jeff-new-dsktp kernel: [ 9853.387576] usb 1-2: reset full speed USB device using ohci_hcd and address 6
Apr 14 14:14:09 jeff-new-dsktp kernel: [ 9853.593818] sd 9:0:0:0: [sde] Write Protect is off
Apr 14 14:14:09 jeff-new-dsktp kernel: [ 9853.611736] sd 9:0:0:0: [sde] 15600 512-byte hardware sectors (8 MB)







dmesg showed:

[ 7740.163112] sd 6:0:0:0: [sdf] Attached SCSI removable disk
[ 7740.163193] sd 6:0:0:0: Attached scsi generic sg5 type 0
[ 8115.962501] [fglrx:firegl_addmap] *ERROR* existing map 0xf6733000 (handle 0x00000000)
[ 8115.962793] [fglrx:firegl_addmap] *ERROR* existing map 0xf6733040 (handle 0xf9240000)
[ 8115.962947] [fglrx] total      GART = 130023424
[ 8115.962952] [fglrx] free       GART = 112066560
[ 8115.962957] [fglrx] max single GART = 112066560
[ 8115.962962] [fglrx] total      LFB  = 134217728
[ 8115.962966] [fglrx] free       LFB  = 80080896
[ 8115.962971] [fglrx] max single LFB  = 80080896
[ 8115.962975] [fglrx] total      Inv  = 0
[ 8115.962979] [fglrx] free       Inv  = 0
[ 8115.962983] [fglrx] max single Inv  = 0
[ 8115.962987] [fglrx] total      TIM  = 0
[ 8310.238669] usb 3-5: usbfs: USBDEVFS_CONTROL failed cmd f-spot rqt 128 rq 6 len 1000 ret -110
[ 8311.249728] usb 3-5: usbfs: USBDEVFS_CONTROL failed cmd f-spot rqt 128 rq 6 len 1000 ret -110
[ 8723.010224] usb 3-5: USB disconnect, address 6
[ 8737.162612] usb 1-2: USB disconnect, address 3
[ 9201.585002] usb 1-2: new full speed USB device using ohci_hcd and address 4
[ 9201.793987] usb 1-2: configuration #1 chosen from 1 choice
[ 9201.796023] scsi7 : SCSI emulation for USB Mass Storage devices
[ 9201.796284] usb-storage: device found at 4
[ 9201.796287] usb-storage: waiting for device to settle before scanning
[ 9206.792181] usb-storage: device scan complete
[ 9206.798171] scsi 7:0:0:0: Direct-Access     SAMSUNG  DIGIMAX 130      1.33 PQ: 0 ANSI: 0 CCS
[ 9206.808138] sd 7:0:0:0: [sde] 15600 512-byte hardware sectors (8 MB)
[ 9236.953565] usb 1-2: reset full speed USB device using ohci_hcd and address 4
[ 9267.303151] usb 1-2: reset full speed USB device using ohci_hcd and address 4
[ 9297.652708] usb 1-2: reset full speed USB device using ohci_hcd and address 4
[ 9328.002281] usb 1-2: reset full speed USB device using ohci_hcd and address 4
[ 9358.351850] usb 1-2: reset full speed USB device using ohci_hcd and address 4
[ 9388.701423] usb 1-2: reset full speed USB device using ohci_hcd and address 4
[ 9388.908663] sd 7:0:0:0: [sde] Write Protect is off
[ 9388.908680] sd 7:0:0:0: [sde] Mode Sense: 55 53 42 53
[ 9388.908685] sd 7:0:0:0: [sde] Assuming drive cache: write through
[ 9388.929234] sd 7:0:0:0: [sde] 15600 512-byte hardware sectors (8 MB)
[ 9419.075001] usb 1-2: reset full speed USB device using ohci_hcd and address 4
[ 9449.428542] usb 1-2: reset full speed USB device using ohci_hcd and address 4
[ 9479.478480] usb 1-2: USB disconnect, address 4
[ 9479.478494] sd 7:0:0:0: [sde] Write Protect is off
[ 9479.478500] sd 7:0:0:0: [sde] Mode Sense: 55 53 42 53
[ 9479.478503] sd 7:0:0:0: [sde] Assuming drive cache: write through
[ 9479.478511]  sde:<6>sd 7:0:0:0: [sde] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 9479.481339] end_request: I/O error, dev sde, sector 0
[ 9479.481344] printk: 5 messages suppressed.
[ 9479.481348] Buffer I/O error on device sde, logical block 0
[ 9479.482189] sd 7:0:0:0: [sde] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 9479.482195] end_request: I/O error, dev sde, sector 0
[ 9479.482197] Buffer I/O error on device sde, logical block 0
[ 9479.482403] sd 7:0:0:0: [sde] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 9479.482407] end_request: I/O error, dev sde, sector 0
[ 9479.482410] Buffer I/O error on device sde, logical block 0
[ 9479.483937] sd 7:0:0:0: [sde] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 9479.483944] end_request: I/O error, dev sde, sector 0
[ 9479.483947] Buffer I/O error on device sde, logical block 0
[ 9479.484550] sd 7:0:0:0: [sde] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 9479.484555] end_request: I/O error, dev sde, sector 0
[ 9479.484557] Buffer I/O error on device sde, logical block 0
[ 9479.484565] ldm_validate_partition_table(): Disk read failed.
[ 9479.485257] sd 7:0:0:0: [sde] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 9479.485262] end_request: I/O error, dev sde, sector 0
[ 9479.485265] Buffer I/O error on device sde, logical block 0
[ 9479.485809] sd 7:0:0:0: [sde] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 9479.485814] end_request: I/O error, dev sde, sector 0
[ 9479.485817] Buffer I/O error on device sde, logical block 0
[ 9479.486360] sd 7:0:0:0: [sde] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 9479.486365] end_request: I/O error, dev sde, sector 0
[ 9479.486368] Buffer I/O error on device sde, logical block 0
[ 9479.486396] sd 7:0:0:0: [sde] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 9479.486400] end_request: I/O error, dev sde, sector 0
[ 9479.486403] Buffer I/O error on device sde, logical block 0
[ 9479.486414] Dev sde: unable to read RDB block 0
[ 9479.487632] sd 7:0:0:0: [sde] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 9479.487637] end_request: I/O error, dev sde, sector 0
[ 9479.487640] Buffer I/O error on device sde, logical block 0
[ 9479.488191] sd 7:0:0:0: [sde] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 9479.488196] end_request: I/O error, dev sde, sector 0
[ 9479.488599] sd 7:0:0:0: [sde] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 9479.488604] end_request: I/O error, dev sde, sector 24
[ 9479.489021] sd 7:0:0:0: [sde] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 9479.489026] end_request: I/O error, dev sde, sector 24
[ 9479.489439] sd 7:0:0:0: [sde] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 9479.489446] end_request: I/O error, dev sde, sector 0
[ 9479.490026] sd 7:0:0:0: [sde] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 9479.490035] end_request: I/O error, dev sde, sector 0
[ 9479.490052]  unable to read partition table
[ 9479.490471] sd 7:0:0:0: [sde] Attached SCSI removable disk
[ 9479.490543] sd 7:0:0:0: Attached scsi generic sg4 type 0
[ 9534.731029] usb 1-2: new full speed USB device using ohci_hcd and address 5
[ 9534.940013] usb 1-2: configuration #1 chosen from 1 choice
[ 9534.942048] scsi8 : SCSI emulation for USB Mass Storage devices
[ 9534.942306] usb-storage: device found at 5
[ 9534.942310] usb-storage: waiting for device to settle before scanning
[ 9539.938210] usb-storage: device scan complete
[ 9539.944198] scsi 8:0:0:0: Direct-Access     SAMSUNG  DIGIMAX 130      1.33 PQ: 0 ANSI: 0 CCS
[ 9539.954162] sd 8:0:0:0: [sde] 15600 512-byte hardware sectors (8 MB)
[ 9570.099570] usb 1-2: reset full speed USB device using ohci_hcd and address 5
[ 9600.449181] usb 1-2: reset full speed USB device using ohci_hcd and address 5
[ 9630.798734] usb 1-2: reset full speed USB device using ohci_hcd and address 5
[ 9637.587945] usb 1-2: USB disconnect, address 5
[ 9637.588366] sd 8:0:0:0: [sde] Write Protect is off
[ 9637.588372] sd 8:0:0:0: [sde] Mode Sense: 55 53 42 53
[ 9637.588377] sd 8:0:0:0: [sde] Assuming drive cache: write through
[ 9637.591913] sd 8:0:0:0: [sde] READ CAPACITY failed
[ 9637.591920] sd 8:0:0:0: [sde] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 9637.591926] sd 8:0:0:0: [sde] Sense not available.
[ 9637.592798] sd 8:0:0:0: [sde] Write Protect is off
[ 9637.592806] sd 8:0:0:0: [sde] Mode Sense: 00 00 00 00
[ 9637.592809] sd 8:0:0:0: [sde] Assuming drive cache: write through
[ 9637.592909] sd 8:0:0:0: [sde] READ CAPACITY failed
[ 9637.592914] sd 8:0:0:0: [sde] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 9637.592920] sd 8:0:0:0: [sde] Sense not available.
[ 9637.592936] sd 8:0:0:0: [sde] Write Protect is off
[ 9637.592941] sd 8:0:0:0: [sde] Mode Sense: 00 00 00 00
[ 9637.592945] sd 8:0:0:0: [sde] Assuming drive cache: write through
[ 9637.593011] sd 8:0:0:0: [sde] Attached SCSI removable disk
[ 9637.593082] sd 8:0:0:0: Attached scsi generic sg4 type 0
[ 9666.279157] usb 1-2: new full speed USB device using ohci_hcd and address 6
[ 9666.488136] usb 1-2: configuration #1 chosen from 1 choice
[ 9666.490163] scsi9 : SCSI emulation for USB Mass Storage devices
[ 9666.490439] usb-storage: device found at 6
[ 9666.490443] usb-storage: waiting for device to settle before scanning
[ 9671.486330] usb-storage: device scan complete
[ 9671.492327] scsi 9:0:0:0: Direct-Access     SAMSUNG  DIGIMAX 130      1.33 PQ: 0 ANSI: 0 CCS
[ 9671.502291] sd 9:0:0:0: [sde] 15600 512-byte hardware sectors (8 MB)
[ 9701.647690] usb 1-2: reset full speed USB device using ohci_hcd and address 6
[ 9731.997272] usb 1-2: reset full speed USB device using ohci_hcd and address 6
[ 9762.334863] usb 1-2: reset full speed USB device using ohci_hcd and address 6
[ 9792.688427] usb 1-2: reset full speed USB device using ohci_hcd and address 6
[ 9823.038017] usb 1-2: reset full speed USB device using ohci_hcd and address 6
[ 9853.387576] usb 1-2: reset full speed USB device using ohci_hcd and address 6
[ 9853.593818] sd 9:0:0:0: [sde] Write Protect is off
[ 9853.593828] sd 9:0:0:0: [sde] Mode Sense: 55 53 42 53
[ 9853.593833] sd 9:0:0:0: [sde] Assuming drive cache: write through
[ 9853.611736] sd 9:0:0:0: [sde] 15600 512-byte hardware sectors (8 MB)
[ 9883.757132] usb 1-2: reset full speed USB device using ohci_hcd and address 6
[ 9896.943970] usb 1-2: USB disconnect, address 6
[ 9896.944161] sd 9:0:0:0: [sde] Write Protect is off
[ 9896.944167] sd 9:0:0:0: [sde] Mode Sense: 55 53 42 53
[ 9896.944171] sd 9:0:0:0: [sde] Assuming drive cache: write through
[ 9896.944178]  sde:<6>sd 9:0:0:0: [sde] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 9896.944427] end_request: I/O error, dev sde, sector 0
[ 9896.944432] printk: 5 messages suppressed.
[ 9896.944437] Buffer I/O error on device sde, logical block 0
[ 9896.944598] sd 9:0:0:0: [sde] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 9896.944605] end_request: I/O error, dev sde, sector 0
[ 9896.944609] Buffer I/O error on device sde, logical block 0
[ 9896.944694] sd 9:0:0:0: [sde] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 9896.944756] end_request: I/O error, dev sde, sector 0
[ 9896.944760] Buffer I/O error on device sde, logical block 0
[ 9896.944977] sd 9:0:0:0: [sde] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 9896.944983] end_request: I/O error, dev sde, sector 0
[ 9896.944986] Buffer I/O error on device sde, logical block 0
[ 9896.945205] sd 9:0:0:0: [sde] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 9896.945211] end_request: I/O error, dev sde, sector 0
[ 9896.945215] Buffer I/O error on device sde, logical block 0
[ 9896.945228] ldm_validate_partition_table(): Disk read failed.
[ 9896.945461] sd 9:0:0:0: [sde] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 9896.945467] end_request: I/O error, dev sde, sector 0
[ 9896.945471] Buffer I/O error on device sde, logical block 0
[ 9896.947915] sd 9:0:0:0: [sde] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 9896.947927] end_request: I/O error, dev sde, sector 0
[ 9896.947933] Buffer I/O error on device sde, logical block 0
[ 9896.949778] sd 9:0:0:0: [sde] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 9896.949789] end_request: I/O error, dev sde, sector 0
[ 9896.949794] Buffer I/O error on device sde, logical block 0
[ 9896.950377] sd 9:0:0:0: [sde] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 9896.950385] end_request: I/O error, dev sde, sector 0
[ 9896.950388] Buffer I/O error on device sde, logical block 0
[ 9896.950399] Dev sde: unable to read RDB block 0
[ 9896.951054] sd 9:0:0:0: [sde] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 9896.951063] end_request: I/O error, dev sde, sector 0
[ 9896.951066] Buffer I/O error on device sde, logical block 0
[ 9896.951675] sd 9:0:0:0: [sde] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 9896.951684] end_request: I/O error, dev sde, sector 0
[ 9896.951895] sd 9:0:0:0: [sde] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 9896.951901] end_request: I/O error, dev sde, sector 24
[ 9896.952449] sd 9:0:0:0: [sde] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 9896.952458] end_request: I/O error, dev sde, sector 24
[ 9896.952834] sd 9:0:0:0: [sde] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 9896.952842] end_request: I/O error, dev sde, sector 0
[ 9896.953215] sd 9:0:0:0: [sde] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 9896.953223] end_request: I/O error, dev sde, sector 0
[ 9896.953232]  unable to read partition table
[ 9896.953726] sd 9:0:0:0: [sde] Attached SCSI removable disk
[ 9896.953800] sd 9:0:0:0: Attached scsi generic sg4 type 0
[ 9978.018634] usb 1-2: new full speed USB device using ohci_hcd and address 7
[ 9978.227618] usb 1-2: configuration #1 chosen from 1 choice
[ 9978.229649] scsi10 : SCSI emulation for USB Mass Storage devices
[ 9978.229903] usb-storage: device found at 7
[ 9978.229907] usb-storage: waiting for device to settle before scanning
[ 9983.225811] usb-storage: device scan complete
[ 9983.231806] scsi 10:0:0:0: Direct-Access     SAMSUNG  DIGIMAX 130      1.33 PQ: 0 ANSI: 0 CCS
[ 9983.241770] sd 10:0:0:0: [sde] 15600 512-byte hardware sectors (8 MB)
[10013.387180] usb 1-2: reset full speed USB device using ohci_hcd and address 7
[10043.744743] usb 1-2: reset full speed USB device using ohci_hcd and address 7
jeff@jeff-new-dsktp:~$

---

### Post by jeffsa12 on 2008-04-15
bump this up

---

### Post by strabes on 2008-04-15
Please don't post duplicate threads. This thread is a duplicate of [http://ubuntuforums.org/showthread.php?t=756006](http://ubuntuforums.org/showthread.php?t=756006)

---

### Post by wolfen69 on 2008-04-15
try opening gthumb image viewer, then go to file>import photos. see if anything happens.

---

### Post by jeffsa12 on 2008-04-15
Thanks wolfen69,

Yea I already tried that and the KDE digital cam package. Neither one shows a camera available. With gthumb, the camera choice in import locations is grayed out and non functional. 

I believe that the scsi file system in the cam? could be a problem...or Ubuntu is not properly mounting the device or able to handle scsi fs.. 

Like I said above, it just shows up as if it's a USB thumb drive in windows explore,  and the file has jpeg pics that I can set as thumbnails....copy etc, etc.

Also worth mentioning is when I got it to work in my VBox in Ubuntu - WinXP, I had to set VBox settings to use USB 1.1 only. It would not mount when I had EHCI USB 2.0 enabled.

---

