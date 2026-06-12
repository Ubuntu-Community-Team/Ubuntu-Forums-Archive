---
title: "installing linux"
date: 2017-03-19
forum: General Help
---

### Post by leilton on 2017-03-19
Hi,   I am a complete novice on all things computer,know enough to be able to install the version I wanted (Ubuntu), on to my refurbished HP Compaq 6910 64 bit, (which when purchased had no system installed at my request.).
As I had always,previous to this, had Bodhi installed, assumed that all I had to do was download and burn to disc, how silly can I be.   (Ubuntu disc was left over from machine that crashed).
I understand that there has been a change in the way you install now, but it leaves me absolutely stymied when I try to understand the instructions.  Is there not a simple way,or a way an ignoramus can understand?
Hopefully made myself clear
Informed when I made purchase that machine was running BIOS not something called :confused:?

---

### Post by poorguy on 2017-03-19
This may help.

[https://www.ubuntu.com/download/desktop/install-ubuntu-desktop](https://www.ubuntu.com/download/desktop/install-ubuntu-desktop)

Page 9 using below link.

[http://files.ubuntu-manual.org/manuals/getting-started-with-ubuntu/16.04/en_US/screen/Getting%20Started%20with%20Ubuntu%2016.04.pdf](http://files.ubuntu-manual.org/manuals/getting-started-with-ubuntu/16.04/en_US/screen/Getting%20Started%20with%20Ubuntu%2016.04.pdf)

Hope this helps.

---

### Post by lysander6662 on 2017-03-19
> **leilton said:**
> 
Informed when I made purchase that machine was running BIOS not something called :confused:? 

Don't quite understand this part - the BIOS is firmware located in a motherboard processor chip that manages data transfer between your hardware and your operating system. It's not a desktop operating system. When you turn your computer on your BIOS will boot either from your hard disk [your operating system of choice], your DVD drive or a flash drive depending on what priority has been defined.

Back when I first started messing around with Linux I installed from DVD too. But now you can install from DVD disk or a USB flash drive. The latter is very quick and necessitates downloading an iso file of the operating system you want and then creating a bootable flash drive via a program like Startup Disk Creator. However, if you are using a DVD, the latest iso should be burned to DVD and then the DVD should be run via the instructions that poorguy linked to. If, when you restart the computer, it doesn't boot from the DVD you may have to go into the BIOS to change boot priority [but we may not have to get into that].

---

### Post by saiyon on 2017-03-19
If you only have access to a windows machine download and install this program:

[https://rufus.akeo.ie/](https://rufus.akeo.ie/)

This will allow you to turn a USB thumb drive into an installation disk by writing the ubuntu .iso file to it.

Basically: 

- Download the Ubuntu .iso (image) file here: [https://www.ubuntu.com/download/desktop](https://www.ubuntu.com/download/desktop)
- Use Rufus to put that image file on a usb thumb drive (you will need a 2GB or larger usb thumb drive)
- boot your PC with the thumb drive inserted, you may need to hit a key such as "del" to boot via the usb thumb drive
- Once you boot from the usb thumb drive follow the instructions to install Ubuntu

Hope that helps...

---

### Post by gordintoronto on 2017-03-19
This 10-year-old computer probably will not deliver acceptable performance with Ubuntu Desktop. You should consider Xubuntu, Ubuntu Mate or Lubuntu.

---

