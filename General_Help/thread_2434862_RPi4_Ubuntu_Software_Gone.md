---
title: "RPi4 Ubuntu Software Gone"
date: 2020-01-12
forum: General Help
---

### Post by multibuild on 2020-01-12
Hey guys,
I have another issue...

I was unable to get Ubuntu Software to install anything without an error, so I heeded the advice of a forum member in uninstalling and reinstalling the gnome-software.

[B]Bad Idea!

[/B]I am unable to reinstall gnome-software and Ubuntu Software is gone.

I have tried many things including:
> sudo apt-get install software-center
and:
> sudo apt-get install gnome-software

In return I get the following:
> ubuntu@rpi4:~$ sudo apt-get install gnome-softwareReading package lists... Done
Building dependency tree       
Reading state information... Done
Package gnome-software is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source


E: Package 'gnome-software' has no installation candidate

 

I would love to have Ubuntu Software back, so any help would be greatly appreciated.  
Thanks!

---

### Post by HermanAB on 2020-01-13
Well, RPi software resides on a SD card.  Simply download the image e.g. (Raspbian), copy to the SD card, plug the SD card into the Rpi and switch it on.  

Here is a guide for Rpi version 3:
[https://www.aeronetworks.ca/2017/12/raspberrypi-3-headless-with-ssh.html](https://www.aeronetworks.ca/2017/12/raspberrypi-3-headless-with-ssh.html)

---

### Post by multibuild on 2020-01-13
Thanks for the help Herman!

I realize I may not have worded this in the best way possible. I accidentally uninstalled the Ubuntu Software Center for downloading packages, when I uninstalled the gnome-software package to try to fix Ubuntu Software not working. Now I can't seem to get it back.

---

### Post by HermanAB on 2020-01-13
In my experience when the Debian/Ubuntu software installation system fails, it can be well nigh impossible to repair.  Downloading packages manually is also not an option, due to the way that Debian/Ubuntu keep all packages in one gigantic repository - you cannot manually step through a FTP directory tree and look for stuff as on a Redhat system.

So, I would re-install the whole thing.  It only takes about 30 minutes - much less time than you have already spent banging your head on the wall over this...

---

### Post by multibuild on 2020-01-14
Thanks.  

I'll do this.

---

