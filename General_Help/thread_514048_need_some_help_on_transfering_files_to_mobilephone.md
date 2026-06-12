---
title: "need some help on transfering files to mobilephone (connecting failed with obexftp)"
date: 2007-07-31
forum: General Help
---

### Post by leeyee on 2007-07-31
Hi guys,

I'm trying to send files to Nokia N70 via obexftp with CA-53 USB cable, but got connecting failed error. However, I've managed it as a GPRS modem to connect Internet with both PPP and wvdial.

The N70 was recognized as /dev/ttyACM0 in my box, but when I type
```
obexftp -t /dev/ttyACM0 -l
```
I was told connecting failed, and it tried again and again with errors. I've googled a lot and followed obexftp example, sitll cannot get it working fine. Following is lsusb output:
```
leeyee@alimus> lsusb 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 0421:0443 Nokia Mobile Phones 
Bus 001 Device 003: ID 046d:c00f Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000 
``` 
And this is output given by dmesg:
```
leeyee@alimus> dmesg | tail
[ 9227.844000] usb 1-2: new full speed USB device using uhci_hcd and address 4
[ 9228.016000] usb 1-2: configuration #1 chosen from 1 choice
[ 9228.760000] cdc_acm 1-2:1.8: ttyACM0: USB ACM device
[ 9228.764000] usbcore: registered new interface driver cdc_acm
[ 9228.764000] drivers/usb/class/cdc-acm.c: v0.25:USB Abstract Control Model driver for USB modems and ISDN adapters

```

And by the way, I've installed gnome-vfs-obexftp, after type "obex:///" in nautilus, it gives a blank entries. Anyone can help out? 

Thanks! Any help will be highly appreciated!

---

### Post by leeyee on 2007-08-01
Things seem to be better now, I've figured mount it with obexfs and fuse, just did following steps:
```
leeyee@alimus> sudo mkdir /mnt/NOKIA
leeyee@alimus> sudo -s
leeyee@alimus> obexfs -u 1 -- /mnt/NOKIA
```

After this, RSMMC contents will be mounted to /mnt/NOKIA, then you can cd into it in the terminal and do what you want to.

However, I'm still trying to find some way to do the same thing with nautilus. For more details, just type
```
man obexfs
man obexftp
man fusermount
```

---

### Post by Arjunanda on 2007-11-13
Thanks for this tip, will try it today. I have been using obex-ftp-frontend, which is a Java GUI over obexftp, but would prefer Nautilus over it. Are you saying manually mounting the phone /mnt/NOKIA does not however display correctly in Nautilus?

---

