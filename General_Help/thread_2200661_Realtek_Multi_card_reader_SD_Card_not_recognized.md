---
title: "Realtek Multi card reader SD Card not recognized"
date: 2014-01-20
forum: General Help
---

### Post by pouldney on 2014-01-20
I have an   Acer AXC-605 Desktop PC .The built in SD card reader was not working
   It did work in Windows8.

   I am using ubuntu 12.04     3.8.0-35-generic

      It is a Realtek Multi-card reader
 Bus 003 Device 004: ID 0bda:0129 Realtek Semiconductor Corp. 
 bDeviceClass          255 Vendor Specific Class
  bDeviceSubClass       255 Vendor Specific Subclass
  bDeviceProtocol       255 Vendor Specific Protocol
  bMaxPacketSize0        64
  idVendor           0x0bda Realtek Semiconductor Corp.
  idProduct          0x0129 
  bcdDevice           39.60
  iManufacturer           1 Generic
  iProduct                2 USB2.0-CRW
  iSerial                 3 20100201396000000
  bNumConfigurations      1


           
I was able to get the driver rts5139.tar.bz2 from:
[http://ubuntuone.com/p/153B/](http://ubuntuone.com/p/153B/)

       After extracting
 I installed it using instructions in README.txt

  The reader was recognized but it would not recognize an
 inserted card.

  I found a patch at
 [http://permalink.gmane.org/gmane.linux.kernel/1500485](http://permalink.gmane.org/gmane.linux.kernel/1500485)

   The patch command would not work so I changed the following lines 
 of file  rts51x_transport.c   Manually

-             status, 2, urb_done_completion, &urb_done, 1);
+             status, 2, urb_done_completion, &urb_done, 10);

-    result = rts51x_msg_common(chip, chip->usb->intr_urb, 50);
+    result = rts51x_msg_common(chip, chip->usb->intr_urb, 100);



 I then re-did the instructions in README.txt
 after re-booting the card worked.

---

