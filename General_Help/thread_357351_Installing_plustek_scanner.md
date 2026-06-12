---
title: "Installing plustek scanner"
date: 2007-02-09
forum: General Help
---

### Post by f1renz on 2007-02-09
[SIZE="2"][FONT="Arial Black"]Hi I have an old scanner ---Plustek OpticPro P12-- and have been trying to install for use without any luck (IT is a parallel port device)
I'm using Ubuntu 6.10(edgy eft) on a AMD Athlon 2300Mhz, 256MB,  

XSane Image Scanner keeps saying "no devices available" 

Tried using back-end ports and even adjusted the /etc/sane.d/dll.conf file so that plustek_pp wasn't commented out with #.

The install cd for the device is meant to run on windows 95/98/ME/NT4.0/2000Professional and so is totally useless here
Is it that sane doesn't have the drivers for this?[/FONT][/SIZE]

---

### Post by f1renz on 2007-02-10
Ok. Since last post, i've been reading and searching with still no luck.

Here are some of the sources i tried:

SANE Frequently asked questions
[HTML]http://www.xs4all.nl/~ljm/SANE-faq.html[/HTML]

Sane Project
[HTML]http://www.sane-project.org/[/HTML]

Scanner HOW TO
[HTML]http://tldp.org/HOWTO/Scanner-HOWTO/index.html[/HTML]

I've also read some of the similar issues with trying to work scanners on linux on Ubuntu's forum

I recommend if anyone has similar issues to first check out sane project website. Once there check their supported devices link to see if your device is supported (other optical devices like cameras may be supported).

Download either the full sane-backend file (latest version) or look for your device and download its backend (driver).

Try also using the terminal 
```
apt-get install sane  
```


If still problems persist check out the Scanner HOWTO site. See if you can install the [SIZE="2"]device manually[/SIZE]

Check out the linux manual for your device. Mine was found at 
```
man plustek_pp
```

Check to make sure scanner is not under root user only and change that

If you still have problems then I guess the only thing you can do like me is try again, ask  for help in forums and report bugs (if you think that's the issue) at 

[HTML]http://www.sane-project.org/bugs.html[/HTML]


Right now I'm hoping that the backend file I have from Sane Project will work for my scanner. If so I'll say how it went

---

### Post by f1renz on 2007-02-13
Unfortunately I still have no luck with this install.

ANYONE have any ideas??

---

### Post by Zigi15 on 2008-01-20
Hre's what I did. Download the backend from [http://www.gjaeger.de/scanner/downloads/plustek-usb-0.52-3.tar.gz](http://www.gjaeger.de/scanner/downloads/plustek-usb-0.52-3.tar.gz). If you neeed an earlier version, just go to downloads/  Extract the archive. Then copy the contents of the backend folder to /etc/sane.d . You must be root for this, so ```
sudo nautilus
```. This worked for me, hope it does for you. Or was the plustek backend already included with sane?:confused:

---

### Post by Zigi15 on 2008-01-20
> **Zigi15 said:**
> Hre's what I did. Download the backend from [http://www.gjaeger.de/scanner/downloads/plustek-usb-0.52-3.tar.gz](http://www.gjaeger.de/scanner/downloads/plustek-usb-0.52-3.tar.gz). If you neeed an earlier version, just go to downloads/  Extract the archive. Then copy the contents of the backend folder to /etc/sane.d You must be root for this, so ```
sudo nautilus
``` This worked for me, hope it does for you. Or was the plustek backend already included with sane?:confused: Who knows. That's linux for ya!

---

### Post by editrix on 2008-01-20
You need to edit the file /etc/sane.d/dll.conf and uncomment the plustek line. For some reason, all the parallel port scanners are commented out in this file, which is what the find-scanner searches to find the scanner.

Uncomment by removing the # at the beginning of the line. You'll need to be root to do it.

---

