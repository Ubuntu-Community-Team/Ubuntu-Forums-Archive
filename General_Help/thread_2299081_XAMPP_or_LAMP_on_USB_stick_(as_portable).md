---
title: "XAMPP or LAMP on USB stick (as portable)"
date: 2015-10-15
forum: General Help
---

### Post by alain.roger on 2015-10-15
Hi,

Can you tell me if there is a way to make a webserver LAMp/XAMPP under Linux working on a USB stick ?
i used such solution under windows while i was switching from laptop to laptops and it was great.

i do not want any virtual computer, just to have a standard webserver usable from USB stick for example.

thx.

---

### Post by Lars Noodén on 2015-10-18
Ubuntu should install just fine on a USB stick, though some aspects will be much slower because of the slow write speeds.  Once you have a bootable USB stick you can add a LAMP stack.

---

### Post by alain.roger on 2015-10-18
i know that but this is not what i want. i want to have apache, php, mysql on USB stick and just do like on windows ...so to run apache service from usb stick

---

### Post by tristan16 on 2015-10-18
> **alain.roger said:**
> i know that but this is not what i want. i want to have apache, php, mysql on USB stick and just do like on windows ...so to run apache service from usb stick

So put 2 and 2 together and make 4. Install Ubuntu on a USB stick like Lars said, then install your apache, php, mysql program on it like a normal computer.

Just make sure you set up persistent storage on the USB stick, otherwise it will be reset to a clean install on every boot.

Oh... I re-read your original post, and I think I understand. You want to install your web server programs on the USB stick and run the programs from the USB on any computer.

As far as I know, you can't. Ubuntu packages rely on other packages, which rely on shared libraries, which may or may not rely on other shared libraries. Basically it would be very hard to do so, and I can't find anything saying it's even possible.

A better solution might be to simply use your USB stick as storage for your programs, and just install the programs on the computers you want to use.

---

### Post by sandyd on 2015-10-18
XAMPP has a linux version, try that.
[https://www.apachefriends.org/download.html](https://www.apachefriends.org/download.html)

---

### Post by sudodus on 2015-10-19
> **alain.roger said:**
> i know that but this is not what i want. i want to have apache, php, mysql on USB stick and just do like on windows ...so to run apache service from usb stick

Ubuntu and Ubuntu Server treat a USB drive as any other mass storage device, so like an internal drive. You can install anything you want*) to a USB drive, just like you install it to an internal drive. But it will be slower in a USB 2 port. It will be fairly fast in a USB 3 port, particularly if you get a [fast USB 3 pendrive](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites) (or SSD in an enclosure).

If you want it portable, you should tweak the network according to the following link

[MinimalInstall#Unmanaged_Wired_Network](https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall#Unmanaged_Wired_Network)

and you should avoid proprietary drivers.

[hr][/hr]
*) Edit: I mean install any version of Ubuntu into a USB pendrive, in this case Ubuntu Server, or if you prefer a desktop flavour of Ubuntu, for example Lubuntu, and install the services you want, apache, php, mysql, into that operating system.

---

### Post by alain.roger on 2015-10-19
> **tristan16 said:**
> So put 2 and 2 together and make 4. Install Ubuntu on a USB stick like Lars said, then install your apache, php, mysql program on it like a normal computer.

Just make sure you set up persistent storage on the USB stick, otherwise it will be reset to a clean install on every boot.

this is exactly what i'm trying to avoid... as later on to debug a PHP or any javascript file using eclipse IDE for example is not stable due to not belonging to the same machine. Eclipse has som issue with remote debugging.

> **sandyd said:**
> XAMPP has a linux version, try that.
[https://www.apachefriends.org/download.html](https://www.apachefriends.org/download.html)

AFAIK Xampp rely on OS librairies and then even if i installed it on USB stick, it will rely on other OS librairies.
So if on the computer i have another OS distro (or another version of the same distro) it may not work.

Or do you have any other information i do not have ? if it was perfectly independent from OS librairies i would be glad.

---

### Post by pqwoerituytrueiwoq on 2015-10-19
you can use a [FTP client]("https://addons.mozilla.org/en-us/firefox/addon/fireftp/") to edit it on your local system?
* it has a sftp protocol so you can just use SSH ([openssh-server](apt:openssh-server))

You could setup a virtualbox install on the usb stick and boot that and on that note you CAN put a real install on the USB and boot it in a virtualbox
as long as the VDI file is on the USB you can add it as a existing virtual HDD in any virtualbox install

---

