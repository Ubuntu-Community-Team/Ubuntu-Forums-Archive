---
title: "udev rules on Ubuntu 14.04 - Symlink won't let me mount."
date: 2015-06-08
forum: General Help
---

### Post by imzack2 on 2015-06-08
Hi,  I am trying to set up udev rules so my Compact Flash reader always gets associated to the same device node and mounted to the same place.

I have created a udev rule... and I can see my SYMLINK Node being created in the /dev folder...

But I cannot mount my new NODE....  

Any ideas what I am over looking?  Sorry if it is something simple, I am a newb when it comes to ubuntu.

Also... I see the device coming up as /dev/sdb instead... and automounting to some weird folder names.

Thanks,

Zack

---

### Post by imzack2 on 2015-06-08
I think I just needed to unmount the sdb nodes then my nodes seem to mount...

Is there a way to automatically have the sdb nodes unmount and my SYMLINK nodes mount upon plugging in a device?

---

### Post by imzack2 on 2015-06-08
Or will I have to write a separate script to do this unmounting and mounting?

I did find this... [http://www.axllent.org/docs/view/auto-mounting-usb-storage/](http://www.axllent.org/docs/view/auto-mounting-usb-storage/)

But I cannot follow all of the naming schemes...


I have also found this...

[http://askubuntu.com/questions/350462/using-udev-to-automount-external-hdd](http://askubuntu.com/questions/350462/using-udev-to-automount-external-hdd)

Makes sense on how it creates the directorys needed...  Don't get how the mounting section works though... or if it will in my case..

Is there a way to rmdir on the device being removed as well?








*********************UPDATE****************************************

I did happen to find this site...
[http://wp.dejvino.com/2013/08/linux-udev-usb-automount-script/](http://wp.dejvino.com/2013/08/linux-udev-usb-automount-script/)

But what would I put for the KERNEL field?  I thought the point of udev rules was since you don't know what device know would be assigned (ie SDA, SDB, ETC...)

---

### Post by imzack2 on 2015-06-09
Also, is there anyway to see if my udev rules are being ran?  And if so, if they puke at all?  This might be able to assist in troubleshooting.

---

