---
title: "Ubuntu 12.0.4 on usb-stick resets everything after a restart."
date: 2013-07-10
forum: General Help
---

### Post by KALALEX on 2013-07-10
Hello,

I made a image of a ubuntu 12.0.4 software system.
Using the terminal command and package gddrescue to
do it on other usb sticks. All ok at this point
After booting from the new usb-stick any change i create (ex. system change,create files/folders) on reboot the system has lost all the changes and the files too.
Any ideas ???

---

### Post by sudodus on 2013-07-10
1. Are you making an image of a ***live*** USB stick? Then this live system will not be saved anywhere (unless you made it ***persistent*** live).

2. Or are you making an image of an ***installed system*** from a hard disk drive to a USB stick? In this case changes should be saved.

Are you running it in the computer with the original hard disk drive connected? Did you change the UUIDs of the clone (and the corresponding references in /etc/fstab)? If not, there will probably be confusion between the internal drive and the USB one, and what you write might be written to 'the other drive' and not where you intended to write.

---

### Post by KALALEX on 2013-07-11
I fixed it , i was using the installer of ubuntu to ddrescue.
But i have an other problem , after the ddrescue prosses on a usb-stick(ubuntu system install) to a free usb-stick after i reboot and plug in only the new "ddrescued" usb-stick and boot from it , when it starts up i get orange screen, flashing orange screen , but some times it opens up the login interface moved a left or right and when i type in the password and press enter i freezes then nothing happens and i have to restart the machinge.

_**NOTE**_: That i have updated the installed system(Ubuntu 12.0.4) on the mother usb-stick, before doing the ddrescue prosses.

Any _more_ ideas :confused:


Is it possible that it might be the vga gpu drivers?

---

### Post by sudodus on 2013-07-11
If you make a cloned copy, it should behave exactly as the original system. But it seems it does not. Please describe exactly what you copied and how you copied it (the command line if you remember it).

It also helps if you describe your computer(s): brand name, model, cpu, ram, graphics chip/card.

Please describe why you are doing this cloning with ddrescue. What do you have and what do you want to get? For example:

Do you have a system that is working like it should, so that you are happy with it?
Do you want to run the same system in another computer?
Or do you want to have a backup copy?
Or do you want a portable operating system?

---

### Post by KALALEX on 2013-07-11
First of all i enabled the multiverse and ultiverse then in the terminal the following :

```
sudo apt-get update
sudo apt-get install gddrescue
sudo fdisk -l
sudo ddrescue -v /dev/sda /dev/sdb --force
```

Hardware :
CPU : intel Atom D525 dual core CPU
Chipset : intel NM10 Express chipset
GPU : ATI Mobility Radeon HD7410M
supported rams : 1xDDR3 SODIMM Max. 4GB (installed 2GB)
No inside HDD. Booting from usb (that works)

Brand : Shuttle
Model : XS35GS V2

I am using to ddrescue to make usb-sticks with ubuntu software on them to use them on non inside HDD harware (Think-clients) so just in case that something happens to a stick i will be able just to un-plug and plug-in an other portable ubuntu stick. In order to use the virtual devices that i have created on a server. More generally for virtualization.

---

### Post by sudodus on 2013-07-11
You have a good reason to make cloned copies :-)

1. Are you copying from the boot drive or from another drive?

```
sudo ddrescue -v /dev/sda /dev/sdb --force
```

Which is your boot drive? /dev/sda or /dev/sdc ?

If you copy / clone the active operating system, it might/will change during the process, and the result will be inconsistent. So boot from one (first) drive, copy/clone from a second drive to a third drive.

2. ATI graphics can cause problems, and might need special care with boot options and or proprietary drivers to work well. You can search the internet for linux and your graphics chip/card or ubuntu and your graphics chip/card.

---

### Post by KALALEX on 2013-07-11
Thank you for the help ! :p
I found the solution/solutions to my problem it was the gpu drivers there are some bugs with them and need to chose and download "special drivers" as they are called. But your way the the 3 sticks sounds more logic to me and more safe so ill do that too. Imagine how many weeks it would take me to install update and install the new drivers on every stick and also change /etc/hosts and /etc/hostname !!!!! It saves up to ~40 minutes for every stick.

---

### Post by sudodus on 2013-07-11
I'm glad you have found the main problem and solved it. It will also improve the situation to use "3 sticks" or if I may suggest: That you make an image file to store a master copy with this command

```
[COLOR=#000000][FONT=Ubuntu Mono]sudo ddrescue -v /dev/sda master.img --force[/FONT][/COLOR]
```

and to make copies from it with

```
[COLOR=#000000][FONT=Ubuntu Mono]sudo ddrescue -v master.img /dev/sdb --force[/FONT][/COLOR]
```

Have a look at the following link, where a similar subject is discussed (using dd where you use ddrescue and how to reduce the risk to write to the wrong drive) [Howto make USB boot drives]("http://ubuntuforums.org/showthread.php?t=1958073")

---

