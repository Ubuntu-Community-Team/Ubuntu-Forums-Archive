---
title: "Cloning Ubuntu Drive"
date: 2018-07-30
forum: General Help
---

### Post by jbamford92 on 2018-07-30
Howdy folks,

So ive spent days setting up my HTPC with my Tuner cards and i would like to make a image of the drive because i had so much hassle compiling and building the firmware and kernel for my Tuner cards.  I am running 14.04 what is the best way to image the drive and have a backup?

Thanks

Jack.

---

### Post by monkeybrain20122 on 2018-07-30
fsarchiver, it is in the repo. [http://www.fsarchiver.org/](http://www.fsarchiver.org/)

---

### Post by jbamford92 on 2018-07-30
Wow quick reply thanks :) i will take a look at it. Is it the same process as restoring back from the image also?

---

### Post by monkeybrain20122 on 2018-07-30
> **jbamford92 said:**
> Wow quick reply thanks :) i will take a look at it. Is it the same process as restoring back from the image also?

You need two commands. one to clone, one to restore.

The first one is 

sudo savefs ... (see link above for details)

You can do the cloning when your system is running, so you don't need a live usb to run fsarchiver, but need something to store your image (e.g an external hd or a separate partition)  For "live" cloning like this use the options -a -A with the savefs command.

For restoration you need to run fsarchiver from a live usb, either get the [system rescue cd ]("http://www.system-rescue-cd.org/")or  just boot off a ubuntu live usb and install fsarchiver. Since you don't nee to reboot it is good for your live session (of course you have to install again next time unless your live usb is persistent)

The command  to restore is 
sudo restfs ..

If you just do straight forward cloning and restore and don't need other command line options (e.g --exclude, which exclude directories from being cloned. Since I backed up my data separately, I would exclude a number of directories to cut down the size of the image) There is a easy to use gui for it as well. [https://launchpad.net/~dieterbaum/+archive/ubuntu/qt5-fsarchiver?field.series_filter=trusty](https://launchpad.net/~dieterbaum/+archive/ubuntu/qt5-fsarchiver?field.series_filter=trusty)

---

