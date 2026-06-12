---
title: "Cant print from Ubuntu 6.06 using HP Laserjet 1018"
date: 2007-05-16
forum: General Help
---

### Post by Makkiesse on 2007-05-16
Hi

I have just install Ubuntu 6.06 on my workstation. I also tried to install the driver for HP Laserjet 1018 on the machine. But even after restarting the workstation, I cant print!! 

Anyone, come across this problem?

---

### Post by mitch.c on 2007-05-16
> **Makkiesse said:**
> Hi

I have just install Ubuntu 6.06 on my workstation. I also tried to install the driver for HP Laserjet 1018 on the machine. But even after restarting the workstation, I cant print!! 

Anyone, come across this problem?

That's really not much to go on! How about some details? Do you have other printers installed... do they work? Has printing ever worked? What's the contents of /etc/cups/cupsd.conf? What's the output of lpstat -t?

Help us help you!

-- 
Mitch

---

### Post by Makkiesse on 2007-05-22
The output of lpstat -t is as follows;

scheduler is running
no default destination
device for LaserJet -1020: usb://HP/LaseJet-1020
Printer LaserJet-1020 is idle. enabled since Mon 21 May 2007 2:55 CAT

when I tried using the terminal and typied in: etc/cups/cupsd.conf

access was denied.

Just how do I install this HP printer in Ubuntu 6.06?

---

### Post by mitch.c on 2007-05-22
Make sure the printer is accepting jobs:
```
$ cupsaccept LaserJet-1020
```
Post the output from the command:
```
$ lpstat  -v
```
Try printing a small text file from the shell prompt:
```
$ lp -d LaserJet-1020 /etc/profile
```
What happens?

To post /etc/cups/cupsd.conf, you need to open it with a text editor or cat to the terminal and cut and paste to a post.

Let me know what happens.

---

### Post by Maxster on 2007-06-02
any news on this? is it working?

i got a laserjet 1018, im running ubuntu 7.04

wen i go throught the wizard printer install, it finds my printer (twice:  
*Hp laserjet 1018 (hp laserjet 1018 usb#1* 
and 
*Hp laserjet 1018 (hp laserjet 1018 kp03jadhplip* )

i installed foo2zjs with the ppd file throught the wizard.

finished the wizard reboot and does not print...

thanks to anyone who helps!

---

