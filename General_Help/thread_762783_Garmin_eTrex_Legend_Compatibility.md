---
title: "Garmin eTrex Legend Compatibility"
date: 2008-04-22
forum: General Help
---

### Post by zewrestler on 2008-04-22
I'm looking into getting this GPS.
[http://www.circuitcity.com/ssm/Garmin-eTrex-Legend-Handheld-GPS-Navigation-010-00256-00/sem/rpsm/oid/37488/rpem/ccd/productDetail.do](http://www.circuitcity.com/ssm/Garmin-eTrex-Legend-Handheld-GPS-Navigation-010-00256-00/sem/rpsm/oid/37488/rpem/ccd/productDetail.do)
Does anyone know if it is compatible with Ubuntu?

---

### Post by sizzam on 2008-05-28
I have a Garmin eTrex Legend CX.   I found that I can use it with [gpsbabel]("http://www.gpsbabel.org/"), which is in the repositories.

However, I prefer to use mine in a VirtualBox Windows XP session so that I can use it with [GPS Swiss Army Knife (GSAK)]("http://www.gsak.net/").  If you haven't tried GSAK, check it out, its amazing.  Its a free trial with a nag, with a purchase price of  $25 to register it, but its well worth it (if you're a GeoCacher).

Note that you have to go get the DEB for the 'closed source' version of VirtualBox , as opposed to the Open Source Edition (OSE) version that is in the repositories.   The OSE version does not have USB support.

Also, USBFS is disabled by default in Ubuntu.  If you do install the full version of VirtualBox so that you can use your GPS in a virtual Windows XP session, you have to make this change in Ubuntu for the USB support to work:

```
sudo mkdir /dev/bus/usb/.usbfs
sudo vi /etc/init.d/mountdevsubfs
```
 
Uncomment out the USBFS section so it looks like this:
```

   # Magic to make /proc/bus/usb work
   #
   mkdir -p /dev/bus/usb/.usbfs
   domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
   ln -s .usbfs/devices /dev/bus/usb/devices
   mount --rbind /dev/bus/usb /proc/bus/usb

```

---

### Post by gabak on 2010-06-04
here it explain how to do it

[http://jhau.maliwi.de/linux/gpssw.html](http://jhau.maliwi.de/linux/gpssw.html)

---

