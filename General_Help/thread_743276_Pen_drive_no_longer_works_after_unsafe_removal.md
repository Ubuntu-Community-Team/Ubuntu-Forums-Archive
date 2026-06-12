---
title: "Pen drive no longer works after unsafe removal"
date: 2008-04-02
forum: General Help
---

### Post by m15hun on 2008-04-02
Hi Folks,

I recently plugged in a Lexar 2GB pen drive into my system but during use one of my screwed USB ports let it half fall out. I tried pushing it back in again and rebooting but it isn't showing up.

I even tried booting into the dreaded Windows and sorting it but it's saying that there's a device plugged in but Windows can't recognise it! I also tried a couple of data recovery programs but they can't detect any drive in the port(s)

This drive has some important work related files on and I rather need to rescue it if possible, does anyone have any ideas?

Cheers.

---

### Post by timcredible on 2008-04-02
was it fat, fat16, or fat32 formatted (which is what they all are when you buy them?).  if so, then it could just need to have the filesystem checked and fixed for errors.  in linux, use dosfsck /a <device name of the flashdrive, like sfa1 or whatever>

---

### Post by beyboo on 2008-04-02
i guess there is some secret gnome / kernel code out here 

if (is_unsafe_removal_attempt(*dev_ptr)) 
  if(chomp_chomp(*dev_ptr)) exit(0);
  

on a lighter note ;)

---

### Post by m15hun on 2008-04-03
Thanks for the replies.

I would check the drive for errors but it isn't recognised at all when I plug it in, it's a non entity in the world of my puter :S.

---

### Post by chrisccoulson on 2008-04-03
I bet it is recognised when you plug it in - it just isn't mounting because there are errors on the volume. You  need to run fsck on it. 

```
sudo dosfsck -a /dev/*sdx*
```
...where /dev/*sdx* is the device node for your drive. To get this, just watch your syslog as you plug the drive in.

---

### Post by danwood76 on 2008-04-03
After you plug it in you can look at dmesg for errors:
```

dmesg | tail

```

this will say if and why the device isnt being loaded, it will also give you the /dev/sdx which is required for the previous suggestion.

---

### Post by m15hun on 2008-04-04
Thanks for the advice.

I plugged the device in and watched my syslog but nothing appeared, the device just didn't fire up. I also tried it in other USB ports with no success.

I tried the dmesg and got this:

> [   49.873743] NET: Registered protocol family 10
[   49.874010] lo: Disabled Privacy Extensions
[   49.874296] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   60.387592] eth1: no IPv6 routers present
[ 2913.531260] usb 2-1: USB disconnect, address 3
[ 2946.074083] usb 2-1: new low speed USB device using uhci_hcd and address 4
[ 2946.249691] usb 2-1: configuration #1 chosen from 1 choice
[ 2946.265853] input: Microsoft Basic Optical Mouse as /class/input/input8
[ 2946.265926] input: USB HID v1.10 Mouse [Microsoft Basic Optical Mouse] on usb-0000:00:1d.1-1
[ 3022.879457] hub 5-0:1.0: Cannot enable port 6.  Maybe the USB cable is bad?

I'm starting to think my motherboard is fried but even that wouldn't explain why the pen drive just stopped functioning, would it?

---

### Post by m15hun on 2008-04-09
Anyone have any further pointers?

---

### Post by danwood76 on 2008-04-09
I think when it half fell out you killed the flash drive.
'[ 3022.879457] hub 5-0:1.0: Cannot enable port 6. Maybe the USB cable is bad? '

makes me think there is an issue with the USB stick.
Does your USB mouse work in the USB port you tried to use the stick in?

---

### Post by m15hun on 2008-04-10
Thanks for the help mate. I get a funny feeling you may be right, my mouse works in the port but the pen-drive doesn't work in any now. :confused:

---

