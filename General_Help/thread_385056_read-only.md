---
title: "read-only?"
date: 2007-03-15
forum: General Help
---

### Post by marco87otk on 2007-03-15
Hello everybody, and thanks in advance for your help!

I have an usb.ext3 hdd of 300 gb that i've been using for a long time with ubuntu,
suddently, i cannot remove anything anymore.
So here's the summary:

error:
rm: cannot remove `circuit.htm': Read-only file system

mtab: 
/dev/sda1 /media/usbdisk ext3 rw,nosuid,nodev 0 0

moreover:
sudo chown root /media/usbdisk/
chown: changing ownership of `/media/usbdisk/': Read-only file system
sudo chgrp root /media/usbdisk/
chgrp: changing group of `/media/usbdisk/': Read-only file system

I pretty much don't know what to do!
can anyone enlight me?
Thank you once more,
best regards,

marco

---

### Post by Arby on 2007-03-15
It sounds as if the permissions on your usb drive are being set incorrectly (or not being set). Changing the ownership of the device to root will not help unless you also access it as root. I am assuming you would also like to be able to use this drive as a regular user. Are you mounting the drive manually or does it automount?

If it is automounting then it should mount as /media/yourdrive. Try doing the following in a terminal to check the pemissions of the drive. ```
cd /media
ls -l
```
That should give you the full list of whatever is in /media, including your usb drive. Post the output here if you're not sure.

If I do this on my system I get the following: ```
lrwxrwxrwx  1 root    root    6 2007-03-03 17:13 cdrom -> cdrom0
drwxr-xr-x  2 root    root 4.0K 2007-03-03 17:13 cdrom0
**drwxr-xr-x  8 richard root  16K 1970-01-01 01:00 GIZMO!**
drwxr-xr-x  4 root    root 1.0K 2007-02-22 00:49 sda2
drwxr-xr-x 21 root    root 4.0K 2007-02-22 00:50 sda5
```
Gizmo is a small usb pen drive which I can use as a standard user. You need to pay particular attention to the 'drwxr-xr-x' part. If you don't have those permissions set the same then you need to do so.

```
sudo chmod 755 /media/yourdrive
``` should do it. If your not familiar with the linux permissions system then it's worth taking some time. I still trip over it quite frequently

---

### Post by marco87otk on 2007-03-15
the permission of /media/usbdisk is 777! drwxrwxrwx! 
And yes, I always automonted it, since in ubuntu it works just perfectly!

tnx for your help!

---

### Post by Arby on 2007-03-15
that is strange, I'm afraid I don't know what the problem is then sorry. I was convinced that would be it

---

### Post by marco87otk on 2007-03-15
Unbelivably solved, by mounting manually with a simple sudo mount /media/usbdisk,
let's blame udev? :)

thanks for the help, it was really appreciated!

---

