---
title: "? Usb ?"
date: 2007-01-17
forum: General Help
---

### Post by Elena678 on 2007-01-17
okei, i am back again, I have a problem with my usb stick, when i put it in, i see all files on it, and i can coppy them to my hard disk, 

but when i will coppy somthing from my hard disk to the usb device, or when i will delete somthing, he is doing the whole prosess, and i see on my in de window where is standing what is on my usb, everything is ok, but when i disconnect it, and put it in again, or in an other pc, all deleted files still there on my usb device, and the things i putted on it, are all gone, do somboddy ken help me with this problem.


thanks for your help

greeings

---

### Post by bodhi.zazen on 2007-01-17
How are you disconnecting the device ?

You need to unmount or eject it not simply remove it.

---

### Post by Rhubarb on 2007-01-17
Make sure you empty your trash before you unmount your usb drive.
--> Right click on the bin icon on the lower left corner of the screen, and select "Empty trash".

If that doesn't work, open up your USB disk in Nautilus, press "Ctrl + h" to show all hidden folders and files, then open up the .Trash-YourUserName Folder and delete its contents.

---

### Post by Elena678 on 2007-01-17
> **bodhi.zazen said:**
> How are you disconnecting the device ?

You need to unmount or eject it not simply remove it.

okei, that´s the problem, i just put it in and take it out, how do you need to mount & unmount it?



> **Rhubarb said:**
> Make sure you empty your trash before you unmount your usb drive.
--> Right click on the bin icon on the lower left corner of the screen, and select "Empty trash".

If that doesn't work, open up your USB disk in Nautilus, press "Ctrl + h" to show all hidden folders and files, then open up the .Trash-YourUserName Folder and delete its contents.

thanks for the advice, will also do this ;)

greetings

---

### Post by bodhi.zazen on 2007-01-17
> **Elena678 said:**
> okei, that´s the problem, i just put it in and take it out, how do you need to mount & unmount it?

thanks for the advice, will also do this ;)

greetings

On the desktop, right click the icon, from the pull down menu select unmount or eject.

From the cli,```
sudo umount /media/device_name
```

You may not need sudo here, but it will not hurt ;)

---

### Post by Elena678 on 2007-01-17
> **bodhi.zazen said:**
> On the desktop, right click the icon, from the pull down menu select unmount or eject.

From the cli,```
sudo umount /media/device_name
```

You may not need sudo here, but it will not hurt ;)

okei, now it´s worinkg :)

thanks

---

