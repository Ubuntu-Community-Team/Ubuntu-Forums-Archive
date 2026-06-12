---
title: "Nvidia 96 drivers work on one user account but not another"
date: 2012-11-01
forum: General Help
---

### Post by searchfgold6789 on 2012-11-01
Hi,
I installed Ubuntu a long time ago on an old Dell Latitude D800 - that was when you could install the nvidia-96 package without any problems. But I recently upgraded it to Ubuntu version 12.04, and now nvidia-96 will not install. I was forced to get drivers from [http://www.geforce.com/drivers/results/48996](http://www.geforce.com/drivers/results/48996) and install the .run file. I do believe that the X ABI version has been updated and the drivers have been updated too.
There are two user accounts on that laptop, and the drivers work fine on one account but not the other one... The problems appear to be that the sidebar is not transparent, the application name indicators for the sidebar icons when the mouse rolls over them are not appearing correctly, and the Dash Home will not open.
Posting here in the hopes that someone could explain this behavior and possibly add a solution... thank you!
 - searchfgold6789

---

### Post by MoebusNet on 2012-11-01
The Dell Latitude D800 is problematic under Ubuntu 12.04 as you noted. Mine currently runs the xorg xserver version 10 from Oneiric to be able to use the older nvidia-96.43.20 driver for my Geforce4 Ti 4200 Go 32 Mb AGP 8x video card [NV28] running Lubuntu 12.04.

The driver you are using, nvidia-96.43.23 does not list my video card as supported; are you using the FX5200 from your signature? These are the only video cards listed as supported:

NVS Series
Quadro NVS 50, Quadro NVS 55/280 PCI, Quadro NVS 210, Quadro NVS 280, Quadro NVS 285, Quadro NVS 290, Quadro NVS 295, Quadro NVS 420, Quadro NVS 440, Quadro NVS 450
Quadro NVS Series
Quadro NVS 50, Quadro NVS 55/280 PCI, Quadro NVS 210, Quadro NVS 280, Quadro NVS 285, Quadro NVS 290, Quadro NVS 295, Quadro NVS 420, Quadro NVS 440, Quadro NVS 450

---

### Post by searchfgold6789 on 2012-11-01
Thank you very much for your reply!
This is a different computer that I have listed in my signature. I'm using the exact same video card that you are.
I thought that the list of supported video cards did not change across microscopic version numbers. I will try installing the 96.43.20 driver now and see what happens. 
Again thanks,
 - searchfgold6789

---

### Post by MoebusNet on 2012-11-01
I'm using the Lubuntu 12.04.1 Live CD as my installation media; nouveau appears to be working properly by using the nomodeset boot option.

This is the thread that detailed what I did to use the Oneiric version of xorg xserver to get the nvidia-96.43.20 driver working:

[http://ubuntuforums.org/showthread.php?p=11909048#post11909048](http://ubuntuforums.org/showthread.php?p=11909048#post11909048)

---

### Post by searchfgold6789 on 2012-11-01
Hi,
How would I go about installing the old X.org packages from Oneiric like you did?
 - searchfgold6789

EDIT: Didn't see you post, worked like a charm! Thanks x 100.

---

