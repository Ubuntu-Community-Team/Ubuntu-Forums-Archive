---
title: "Fuji FinePix A210"
date: 2005-08-25
forum: General Help
---

### Post by Ammani on 2005-08-25
Hi,

I have a Fuji FinePix A210 Digital Camera. Does anyone know if I can use this camera on Ubuntu or not since it is not included in the list of supported Cameras. 

Thanks.

---

### Post by jacaetevha on 2007-01-02
My Aunt has one of these.  I haven't gotten it to work with the gphoto library, but it does mount just fine as a USB device.  You can copy and view pictures and if you want to move them off of the camera you just do it as root/sudo or mount the device with the proper user attributes.  It showed up differently on my machine: once as */dev/sdb1* and once as */dev/sdc1*.  The line in **/etc/fstab** I have is:
    ```
/dev/sdb1 <some directory> users,auto 0 0
```
    ```
/dev/sdc1 <some directory> users,auto 0 0
```
Or you can mount it manually with (you might have to do this as root using 'sudo'):
    ```
mount /dev/sdb1 <some directory>
```
Hope that helps.

---

### Post by Doug11 on 2007-01-02
I just bought a finepix a700 and it works great. my Edgy picks up the camera and i can import the pics within. I use Picasa2 for my photo management and have no complaints at all.

---

