---
title: "USB stick access (problems with permissions)"
date: 2015-08-13
forum: General Help
---

### Post by Robbyx on 2015-08-13
My friend's Dell optiplex 745 will not allow access to her to write to her memory sticks unless she  is root!

In media/ the usb directories are usb, usb0, usb1, ...usb7. USB =jane, usb0=root, usb1=root, usb2=jane

Usb has a symlink on it but to where I do not know. However if she puts the usb mem stick into one of the usb sockets the same content can be viewed in the "usb" folder and which ever one from usb1 to 7 has been allocated to the usb stick. I don't know why.

I have tried taking out the usb stick and as root changing the folder  permissions for all the usb directories in /media/ to Jane but they immediately revert to the settings in para 2 above.

Sudo chmod -R 0777 /media/usb1 (ditto to usb7) does not alter the file permissions or the usb directory permissions on  a permanent basis. Thus if I take the usb stick out and put it back in the permissions revert to their original status as above.

Changing the user name and group of the usb  folders by accessing the file manager as root, does not have a permanent effect.


What more can I do?

---

### Post by nerdtron on 2015-08-13
Did you install anything before this happened? 

Hhhmmm.. I'm guessing you installed the usbmount package which is not intended for GUI systems.
```
 sudo apt-get remove usbmount 
```

Then reboot to see if problems persists.

---

### Post by Robbyx on 2015-08-25
We seem to have had some  improvement. Thank you. Now the problem is that she has an external 1tb  usb HD (Samsung). When it is plugged  into the spare usb2 port  on the computer  it is mounted properly. When it is plugged into a 4 port hub it is not being mounted. However if she plugs in a memory stick into the same hub, it is mounted. The Sumsung ext HD is ntfs. The 8gb memory stick is fat32. What is going on?

---

### Post by nerdtron on 2015-08-25
> Now the problem is that she has an **external 1tb  usb HD** (Samsung). When it is** plugged into a 4 port hub** it is not being mounted. However  if she plugs in a** memory stick into the same hub, it is mounted**.

Not a problem on Ubuntu at all. External hard drives needs more power than regular usb sticks. So external hard drives need to be plugged on usb ports (not usb hubs) usually on the back of the computer. USB hubs like 4 ports with no external power source won't be able to support external hard drives due to insufficient power.

---

