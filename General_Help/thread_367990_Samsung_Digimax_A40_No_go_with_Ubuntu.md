---
title: "Samsung Digimax A40: No go with Ubuntu?"
date: 2007-02-22
forum: General Help
---

### Post by andrew.46 on 2007-02-22
Hi,

 I have been trying to get a Samsung Digimax A40 digital camera working with Xubuntu 6.10 with a conspicuous lack of success. There are no drivers provided the manufacturer and Xubuntu does not even recognise it as an external USB drive.

 I have searched google + these forums with no definitive result. Should I just wait until I buy a new camera and research one that works with ubuntu or is there a work-around?

                          Thanks for your trouble,

                                                Andrew

---

### Post by andrew.46 on 2007-02-22
Hi!!

 Oops: found it:

   1. Created a new mount point: $ sudo mkdir /mnt/camera
   2. Mounted the camera: $ sudo mount /dev/sda1 /mnt/camera -t vfat -o umask=000

 I should look a little harder next time!!

                     Andrew

---

