---
title: "&quot;failed to enumerate device in port...&quot; issue when plugging SD cards"
date: 2012-12-11
forum: General Help
---

### Post by gonzobilbao on 2012-12-11
Hi


I've been having this issue since I installed Ubuntu 12.04 (32bit) in my new laptop (an HP envy4 1050ca) a few months ago. It doesnot read SD cards, even when plugged to a an external reader, or directly to the built-in reader.
dmesg command gives the following message

"failed to enumerate device in port #" (# is the port where I had connected my sd cards)

I have tryed a few possible solutions, like installing usbmount, but none worked

Does anybody have any idea on this?

Thank for the help!

---

### Post by gonzobilbao on 2013-01-03
Hi


I've researched more into the issue, it happens that it is a problem concerning xhci_hcd.
The output to
```
tail -f /var/log/syslog
```was

```
usb 3-1: new full-speed USB device number 4 using xhci_hcd
usb 3-1: Device not responding to set address.
usb 3-1: Device not responding to set address.
usb 3-1: device not accepting address 4, error -71
hub 3-0:1.0: unable to enumerate USB device on port 1
```any idea? hope anybdy has any clue about this

thanks

---

### Post by efflandt on 2013-01-03
Are you attempting to connect SDHC or SDXC on a card reader not capable of that?  Does the card reader work for those cards on any other computer or OS?

---

### Post by gonzobilbao on 2013-01-04
All my cards can be read (both using an external reader or the built-in one) under my windows partition

Cheers

---

### Post by gonzobilbao on 2013-02-08
So finally I kinda got on top of this. So I still have the problem with the external reader (although now it only happens sometimes), but I made the built in card reader work just perfect. So

-my external reader works SOMETIMES. I upgraded to linux mint 14 (12.10 based) so I guess the upgrade fixed this partially

-however, the built-in reader continued not to work. When typing *lspci  *in a terminal, the output was 


```
  Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5289 (rev 01)
```This is the sdcard built in reader. If you have this same one  you can solve this by:
 
   
 a)download this package
      [https://bugs.launchpad.net/bugs/971876/+attachment/2991730/+files/rts_bpp.tar.bz2](https://bugs.launchpad.net/bugs/971876/+attachment/2991730/+files/rts_bpp.tar.bz2)

    b) follow these instructions

* In Dolphin (or equivalent) right click and "Extract > Extract Archive here"
* Open a terminal window
* Navigate to Downloads / rts_bpp 
* At the command prompt enter
su root
* Enter root password
* Type the following commands:
make
make install
depmod -a
* To get the driver working instantly type the following or reboot

(see original thread here [http://www.pclinuxos.com/forum/index.php?topic=109447.0](http://www.pclinuxos.com/forum/index.php?topic=109447.0))

And voilá! The card reader works perfectly! I dont know if it will work with other card readers, with mine works just perfect

Hope this helps
Cheers:popcorn:

---

