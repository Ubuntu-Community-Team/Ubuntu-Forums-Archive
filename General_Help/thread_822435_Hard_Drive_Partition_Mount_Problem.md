---
title: "Hard Drive Partition Mount Problem"
date: 2008-06-08
forum: General Help
---

### Post by ne0h on 2008-06-08
I have a 40GB external Hard disk which I used long time (1 year) back. Recently I plugged in it on my ubuntu system through IDE-USB cable. The problem now is I'm not been able to mount all the partitions in the hard drive. Possible reason may be partition corrupted/FS corrupted. Only one partition is getting mounted, others are not. See below -
[IMG]http://ubuntuforums.org/picture.php?albumid=231&pictureid=788[/IMG]

The problem is sdd1, sdd6-9 are not available in /dev - so I can't mount it. 

Available mount points in /dev -
```
# ls /dev | grep sdd
sdd
sdd5

```

System Log:
```
# tail /var/log/messages
Jun  8 17:54:41 ne0h-lappy kernel: [ 5291.490718] usb 5-4: reset high speed USB device using ehci_hcd and address 8
Jun  8 17:55:11 ne0h-lappy kernel: [ 5321.685809] usb 5-4: reset high speed USB device using ehci_hcd and address 8
Jun  8 17:55:14 ne0h-lappy kernel: [ 5324.382358] input: b43-phy0 as /devices/virtual/input/input85
Jun  8 17:55:41 ne0h-lappy kernel: [ 5351.878190] usb 5-4: reset high speed USB device using ehci_hcd and address 8
Jun  8 17:55:41 ne0h-lappy kernel: [ 5352.014245] sd 7:0:0:0: [sdd] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK,SUGGEST_OK
Jun  8 17:55:41 ne0h-lappy kernel: [ 5352.014255] end_request: I/O error, dev sdd, sector 21013436
Jun  8 17:55:41 ne0h-lappy kernel: [ 5352.014259] printk: 1 messages suppressed.
Jun  8 17:57:16 ne0h-lappy kernel: [ 5377.478076] input: b43-phy0 as /devices/virtual/input/input86
Jun  8 17:59:18 ne0h-lappy kernel: [ 5408.650389] input: b43-phy0 as /devices/virtual/input/input87
Jun  8 18:01:20 ne0h-lappy kernel: [ 5443.333575] input: b43-phy0 as /devices/virtual/input/input88

```

DMESG log:
```
# dmesg | tail
[ 5443.333575] input: b43-phy0 as /devices/virtual/input/input88
[ 5443.343129] evdev: no more free evdev devices
[ 5443.343140] input: failed to attach handler evdev to device input88, error: -23
[ 5443.382359] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[ 5443.382368] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 4).
[ 5477.538481] input: b43-phy0 as /devices/virtual/input/input89
[ 5477.548852] evdev: no more free evdev devices
[ 5477.548862] input: failed to attach handler evdev to device input89, error: -23
[ 5477.586519] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[ 5477.586528] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 4).

```

Is there any way to force read the partition so I can recover some of the data (not all) ?

---

### Post by Matthew Wiebelhaus on 2008-06-08
Oh, not sure how to do this on linux but...........if you have a windows computer nearby you can try to read the disk from there but I feel ashamed for recommending this. :popcorn:

---

### Post by VMC on 2008-06-08
What about this error "I/O error, dev sdd, sector 21013436".

Have you tried 'fsck /dev/sddx' on your usb drive?

---

### Post by ne0h on 2008-06-08
> **VMC said:**
> What about this error "I/O error, dev sdd, sector 21013436".

Have you tried 'fsck /dev/sddx' on your usb drive?

ya.. tried once :(

---

