---
title: "Input/output error during write on /dev/sdd"
date: 2016-04-16
forum: General Help
---

### Post by jadeye2 on 2016-04-16
Hello
I have a problem with a **PNY 128GB USB 3.0**.
I can't get access to it, it will not mount and when I tried writing a new partition table with **GParted** I get "Input/output error during write on /dev/sdd"
I tried PNY's tools but with no luck
This is my (tail) syslog:

```
Apr 16 21:33:24 kernel: [ 3860.723445] usb 1-1.3: reset high-speed USB device number 4 using ehci-pci
Apr 16 21:33:55 kernel: [ 3891.681505] usb 1-1.3: reset high-speed USB device number 4 using ehci-pci
Apr 16 21:34:26 kernel: [ 3922.639602] usb 1-1.3: reset high-speed USB device number 4 using ehci-pci
Apr 16 21:34:27 kernel: [ 3923.145320] sd 7:0:0:0: [sdd] Unhandled error code
Apr 16 21:34:27 kernel: [ 3923.145324] sd 7:0:0:0: [sdd]  
Apr 16 21:34:27 kernel: [ 3923.145326] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK
Apr 16 21:34:27 kernel: [ 3923.145327] sd 7:0:0:0: [sdd] CDB: 
Apr 16 21:34:27 kernel: [ 3923.145328] Write(10): 2a 00 0f d9 7f e8 00 00 10 00
Apr 16 21:34:27 kernel: [ 3923.145332] end_request: I/O error, dev sdd, sector 265912296
Apr 16 21:34:27 kernel: [ 3923.145335] Buffer I/O error on device sdd, logical block 33239037
Apr 16 21:34:27 kernel: [ 3923.145336] lost page write due to I/O error on sdd
Apr 16 21:34:27 kernel: [ 3923.145342] Buffer I/O error on device sdd, logical block 33239038
Apr 16 21:34:27 kernel: [ 3923.145343] lost page write due to I/O error on sdd
Apr 16 21:34:27 kernel: [ 3923.145344] Buffer I/O error on device sdd, logical block 33239039
Apr 16 21:34:27 kernel: [ 3923.145345] lost page write due to I/O error on sdd

```

Has anyone manage to fix such a problem?
Thank you

---

