---
title: "An error occurred in the io-library"
date: 2007-04-28
forum: General Help
---

### Post by kfehr911 on 2007-04-28
> An error occurred in the io-library ('Could not claim the USB device'): Could not claim interface 0 (Operation not permitted). Make sure no other program or kernel module (such as sdc2xx, stv680, spca50x) is using the device and you have read/write access to the device.

THis is the error I get when I try to transfer pitures from my camera to the desktop.  I read that it is relitive to the format PTP or mass usb storage but that is not possible with the camera I'm using. Any work arounds that I can explore?

---

### Post by psycosmyth on 2007-05-06
this works, you may have to re-do it_http://ubuntuforums.org/showthread.php?t=388576&page=3&highlight=camera

---

### Post by kfehr911 on 2007-05-14
Excellent!  This fixed the problem quick and easy.  I'm reposting the information and clarifing the details.

Open a Terminal and type:


sudo gedit /etc/udev/rules.d/45-libgphoto2.rules


Comment out the third line  by add a number sign # and add insert DIRECTLY beneath it this:


SUBSYSTEM!="usb_device", GOTO="libgphoto2_rules_end"


Save the file and close Gedit.


When you’re done editing the first five lines should look like:


# udev rules file for libgphoto2 devices (udev < 0.9
#
#BUS!=”usb*”, GOTO=”libgphoto2_rules_end”
SUBSYSTEM!=”usb_device”, GOTO=”libgphoto2_rules_end”
ACTION!=”add”, GOTO=”libgphoto2_rules_end”



Now, restart udev:


sudo /etc/init.d/udev restart


That worked for me.
Note that there are three number signs commenting out those lines. I hope this help in the furture. Cheers

---

