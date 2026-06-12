---
title: "Ubuntu 20.04 infinite loop on reboot, with three services of systemctl"
date: 2020-09-17
forum: General Help
---

### Post by papa0001 on 2020-09-17
Ubuntu Mate 20.04 crashed and enters an infinite loop on reboot, trying and failing to start the following systemctl services: (1) Stystem Logging Service (rsyslog.service), (2) D-Bus Message System Bus (dbus.service) and (3) Login Service. (This is no other OS on the machine)
 
My two question are (my machine has a CD drive):
(1) Isn't there a CD somewhere that will take control of the computer, and fix whatever is wrong? Or,
(2) isn't there a CD somewhere that will take control of the computer, erase absolutely everything, and install a new operating system?
Either of those is all I want.
 
The screen printout is as follows:
[   OK   ] stopped **System Logging Service**
                 starting **System Logging Service**
[FAILED] Failed to start **Login Service**
see 'systemctl status rsyslog.service' for details
[   OK   ] Stopped **Login Service**
[   OK   ] Listening on **D-Bus System Message Bus Socket **
                 Starting **Login Service**
[   OK   ] Started **D-Bus System Message Bus**       *These two lines are repeated five times*
dbus.service                                                          *These two lines are repeated five times*
[FAILED] Failed to start **D-Bus System Message Bus**
see 'systemctl status dbus.service' for details
[FAILED] Failed to start **System Logging Service**
see 'systemctl status rsyslog.service' for details
[   OK   ] Stopped **System Logging Service**
... and so on, over and over.

---

### Post by yapidumoac on 2020-09-17
Using the dvd you originally installed from try following this instructional website:

[try ubuntu before you install]("https://ubuntu.com/tutorials/try-ubuntu-before-you-install")

---

### Post by papa0001 on 2020-09-17
I installed using a USB memory stick.  Now, when I "drop down" to the command line, and go to /media/myname/ls  I see listed a TOSHIBA external hard drive which is no longer connected to the machine, and I do not see the USB stick, which is  now connected to the machine.  The boot USB stick has been in there all this time.  Trying updatedb makes no difference.  I found the GRUB screen where one can set the order of preference for boot source, and placed USB first, but that also does not make a difference.  In other words, the computer does not realize that the USB boot stick is there, and I do not know how to make it aware of it and awaken the boot drive on the USB.  Nevertheless, I have another computer and both can write to CD-ROMs, and I would be very grateful if you could recommend a rescue disk that would solve the problem, even if it means erasing everything in the process.

---

