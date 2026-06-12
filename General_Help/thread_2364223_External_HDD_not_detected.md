---
title: "External HDD not detected"
date: 2017-06-20
forum: General Help
---

### Post by grey1beard on 2017-06-20
One of my external hhd's works fine, but trying the second one (used the same usb cable) is not appearing on my files now. I've not had any problems with it before, so a bit of a puzzle.
I've just run lsusb, and it didn't appear, so I ran **dmesg | tail -n 20** , and got the following.

```
john@john-RM:~$ dmesg | tail -n 20
[ 1436.154005] usb 2-1.2: New USB device strings: Mfr=1, Product=3, SerialNumber=2
[ 1436.154008] usb 2-1.2: Product: USB Mass Storage Device
[ 1436.154011] usb 2-1.2: Manufacturer: Generic     
[ 1436.154014] usb 2-1.2: SerialNumber: 116AC2101219
[ 1436.235332] usb-storage 2-1.2:1.0: USB Mass Storage device detected
[ 1436.235538] scsi host5: usb-storage 2-1.2:1.0
[ 1436.235738] usbcore: registered new interface driver usb-storage
[ 1436.255726] usbcore: registered new interface driver uas
[ 1437.233238] scsi 5:0:0:0: Direct-Access        Mass  Storage Device        PQ: 0 ANSI: 0
[ 1437.233918] sd 5:0:0:0: Attached scsi generic sg3 type 0
[ 1437.234509] sd 5:0:0:0: [sdc] 1250263726 512-byte logical blocks: (640 GB/596 GiB)
[ 1437.235160] sd 5:0:0:0: [sdc] Write Protect is off
[ 1437.235171] sd 5:0:0:0: [sdc] Mode Sense: 03 00 00 00
[ 1437.236431] sd 5:0:0:0: [sdc] No Caching mode page found
[ 1437.236437] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[ 1437.309799]  sdc: sdc1
[ 1437.333325] sd 5:0:0:0: [sdc] Attached SCSI disk
[ 1474.943551] usb 2-1.2: USB disconnect, device number 3
[ 1876.180790] systemd-hostnamed[2437]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[ 2344.895600] systemd-hostnamed[2579]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
john@john-RM:~$ 
```

Can someone guide me through resolving this, if following the last lines of the terminal result is what I need to do ?
If there are alternatives, I'd be grateful for some help.

John

---

### Post by bjlockie on 2017-06-20
It looks it is there as sdc.
Apparently that warning is only misleading.
Is sdc the right drive (640GB)?

---

### Post by grey1beard on 2017-06-20
Yes, I believe that is the correct drive. It's currently inside an enclosure, so I can't get at the serial number to check.
John

---

### Post by grey1beard on 2017-06-21
** No, that's wrong**.
The problem drive is only 250Gb.
I've just run the same code in terminal on another external hdd, and the data that it throws up is exactly the same as the above copy.
So I've no idea how that is going on.
I've double checked, and get the same code on terminal.

---

### Post by grey1beard on 2017-07-14
Well, as I said in the previous post, I've no idea what's going on.
I tried the hdd again this morning, having done nothing to it but leave it on the shelf for three weeks, and now it's OK.
Downloaded some critical art work, and carefully unmounted it, and put it back on the shelf !

---

