---
title: "Ubuntu for Thumb Drive"
date: 2007-06-03
forum: General Help
---

### Post by Cool Surfer on 2007-06-03
Is there a ubuntu version for thumb drive?
It would be great if there is one :)

---

### Post by Sockerdrickan on 2007-06-03
What's a thumb drive? :P

---

### Post by Ek0nomik on 2007-06-03
Yes you can install Ubuntu onto a USB Thumbstick.

Just run the Live CD or Alternate CD and choose that device to install to.

---

### Post by Cool Surfer on 2007-06-03
USB portable thumb drive is ... umm... it is a memory stick and you can boot from it if you change the boot options in your bios to first boot device as usb boot.:p

---

### Post by Sockerdrickan on 2007-06-03
I thought it was called USB-memory


Oh, well :)
[img]http://www.gadgetspy.co.uk/wp-content/photos/usb_thumb_drive.JPG[/img]

EDIT: Yes, that image was to celebrate my 100 post :P

---

### Post by Cool Surfer on 2007-06-03
> **Ek0nomik said:**
> Yes you can install Ubuntu onto a USB Thumbstick.

Just run the Live CD or Alternate CD and choose that device to install to.

hmm... :)
So this is going to be my next ptofect. Got a minidata traveller 2gb Kingston :)

BTW: where will this option appear to use usb drive as target/

---

### Post by Ek0nomik on 2007-06-04
Why?  Are you having problems getting your USB device to be recognized?

If you do it with the Live CD, gparted (your partition editor) should pick up on the device and you should be able to format it into the necessary partitions.

---

### Post by jfinkels on 2007-06-04
> **Cool Surfer said:**
> hmm... :)
So this is going to be my next ptofect. Got a minidata traveller 2gb Kingston :)

BTW: where will this option appear to use usb drive as target/

It will be called something like '/dev/sdb'. To take a look at disks connected to your system, type the following in your terminal:
```
sudo fdisk -l
```This will show all disks and partitions currently plugged in to the system (not necessarily mounted).

---

### Post by jfinkels on 2007-06-04
> **Tux0r said:**
> 
EDIT: Yes, that image was to celebrate my 100 post :P

Disturbing... :P

---

### Post by Cool Surfer on 2007-06-04
I want to boot using thumb drive. As my work place doesnt have ubuntu installed. N i want to use ubuntu. :)

---

