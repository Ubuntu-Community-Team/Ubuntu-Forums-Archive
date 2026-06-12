---
title: "Xbox one controller with KDE Ubunutu"
date: 2018-04-19
forum: General Help
---

### Post by sinqbad on 2018-04-19
I thought that xbox one bluetooth controllers were supposed to work out of the box with Ubuntu? I am running 18.04beta2 and the bluetooth detects the xbox one controller I think but it displays as it's mac address(?). I've tried xpad but I have to go sudo modprobe xpad for it to appear on the lsmod. And when I reboot and exec lsmod it's no longer there. How do I get the xbox one controller working?

---

### Post by deadflowr on 2018-04-19
Try the xboxdrv driver/package.

---

### Post by sinqbad on 2018-04-21
> **deadflowr said:**
> Try the xboxdrv driver/package.

doesn't work either, still the same issue (was the MAC? address and won't connect) is there somewhere that can help me debug xpad?

---

### Post by sinqbad on 2018-04-24
> **deadflowr said:**
> Try the xboxdrv driver/package.

bump

---

### Post by andrelima175 on 2018-05-24
[SIZE=2]You don't need to install xboxdrv. Just use the original xpad that comes with ubuntu/kubuntu. 
If you plug with an usb cable it will recognize out of the box. But if you want to use bluetooth you have to do these tricks. 
I tested this in Ubuntu 18.04 and 16.04. 

Type - "rfkill list" and see if bluetooth is softblocked(if showing 'yes'). 

If so, unblock bluetooth - "sudo rfkill unblock bluetooth". 

[/SIZE][SIZE=2]Then disable ertm: 

[/SIZE][COLOR=#333333][FONT=monospace]- Install sysfsutils. (with synaptic or on terminal)[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]- edit this file with sudo - sudo nano /etc/sysfs.conf[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]- add this line at the end - /module/[/FONT][/COLOR][COLOR=#333333][FONT=monospace]bluetooth/[/FONT][/COLOR][COLOR=#333333][FONT=monospace]parameters/[/FONT][/COLOR][COLOR=#333333][FONT=monospace]disable_[/FONT][/COLOR][COLOR=#333333][FONT=monospace]ertm = 1[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]- reboot.

Thats it. 
 
If your Xbox One S starts to move the mouse do this trick: 

[/FONT][/COLOR][COLOR=#333333][FONT=monospace]- On terminal type - xinput list - and copy how your system recognize the gamepad. Generally is something[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]  like "Xbox Wireless Controller"
[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]- Open a terminal and type - xinput --set-prop "Xbox Wireless Controller" "Device Enabled" 0
[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]- Repeat that second trick every time you got the problem.


Regards! [/FONT][/COLOR]

---

