---
title: "io libary  problems"
date: 2007-05-22
forum: General Help
---

### Post by kfehr911 on 2007-05-22
This was what I had received through a forum about how to correct the problem I was having getting camera to import photos. I had done the following

Open a Terminal and type:


sudo gedit /etc/udev/rules.d/45-libgphoto2.rules


Comment out the third line by add a number sign # and add insert DIRECTLY beneath it this:


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

This worked great in solving the problem for the Sony PowerShot A80 I have but what about the Panasonic DMC-FX8 that my friend has. I'm getting the following error.

An error occurred in the io-library ('Unspecified error'): Could not query kernel driver of device.

At first it loads the drivers from usr/libphoto/libphoto2.3.0. It finds a driver but doesn't connect. I have downloaded through aptitude both gphoto2 and gphotofs and that has not corrected the problem. What step am I missing? What else will I need to do so that I can import these photos from this camera? It is very important to me because I will be using two or three different cameras in the near future. Please help me so that I will not be hung up every time I use a different camera. Will I have to find the proper driver for every camera or is there a genaric one that I could use?Thanks

---

