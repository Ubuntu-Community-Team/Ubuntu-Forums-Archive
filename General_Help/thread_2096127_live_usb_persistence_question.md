---
title: "live usb persistence question"
date: 2012-12-19
forum: General Help
---

### Post by nomadlite on 2012-12-19
if I have a standard live usb xubuntu and then run update and install all latest updates on persistence, will these new update be apply to new hard drive installations?

I just want to know if I can update the live usb then install latest software on 2 computers. Or do I have to install on the computer and download updates separately?

---

### Post by dcstar on 2012-12-19
> **nomadlite said:**
> if I have a standard live usb xubuntu and then run update and install all latest updates on persistence, will these new update be apply to new hard drive installations?

I just want to know if I can update the live usb then install latest software on 2 computers. Or do I have to install on the computer and download updates separately?

AFAIK no, updates only apply to the Live USB system when it is run.

The install uses the files copied from the install CD/Image and will have to be updated.

---

### Post by C.S.Cameron on 2012-12-19
Do not run update manager on a persistent USB.
Max casper-rw, (the persistence file), size is 4GB, Update will quickly fill this.
Once casper-rw is full the drive will not boot.

Casper-rw is ignored when installing from the USB.

Remastersys is one of several applications that can be used to make a custom install iso from a Ubuntu install.

---

### Post by oldfred on 2012-12-19
Several ways to download once.

       Offline Updates:
[http://keryxproject.org/](http://keryxproject.org/)
[https://help.ubuntu.com/community/APTonCD](https://help.ubuntu.com/community/APTonCD)
Download once for many machines
How To Install Apt-Cacher-NG in Ubuntu Linux
[http://ubuntuforums.org/showthread.php?t=981085](http://ubuntuforums.org/showthread.php?t=981085)
Location of downloaded debs, copy to another system
/var/cache/apt/archives/
sudo apt-get install --no-download <package name>

---

### Post by C.S.Cameron on 2012-12-19
Thanks Oldfred:
Download Once looks useful.

The account has been disabled for this link:

[http://keryxproject.org/](http://keryxproject.org/)

---

### Post by oldfred on 2012-12-19
It looks like keryxproject has not been updated since Jan 2011. No idea if it even still works.

       [https://launchpad.net/keryx/+download](https://launchpad.net/keryx/+download)

---

