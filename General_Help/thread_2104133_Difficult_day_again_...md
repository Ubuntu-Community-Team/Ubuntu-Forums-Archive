---
title: "Difficult day again .."
date: 2013-01-12
forum: General Help
---

### Post by longbeard on 2013-01-12
Steaming again ...

Using 12.04 I already mention the surface is somewhat unfortunate. Now it appears to be also the software collection. Was searching for an hour in vain for a usable system analysis tool (incl. the Software-Center). Just want to know what harware is installed on my device. Why is such a thing impossible nowadays? I remember this was easier in previous Ubuntu version. Alas ..!

So I found difficult today:

- there is no introduction to Ubuntu anywhere, also there is no info box informing you what is the website where you can report problems or feedback to the Ubuntu developers. No wonder they don't get near to their users!

- so can you help me out with a system analysis tool? Thanks!
#-o

---

### Post by simvin76 on 2013-01-12
Try lspci. It is in the pciutils package.
[PHP]sudo apt-get install pciutils[/PHP]


Take care
/Simon

---

### Post by dsv47 on 2013-01-12
```
sudo apt-get install sysinfo
```

---

### Post by ibjsb4 on 2013-01-12
You may find this handy for future searches.

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=list+installed+hardware&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=list+installed+hardware&as_qdr=all&sa=Google+Search&lang=en)

---

### Post by Cheesemill on 2013-01-12
> **longbeard said:**
> 
- there is no introduction to Ubuntu anywhere, also there is no info box informing you what is the website where you can report problems or feedback to the Ubuntu developers. No wonder they don't get near to their users!

Have you tried the help application that comes with Ubuntu?

Also all of the official documentation is on the same Ubuntu website that you downloaded Ubuntu from in the first place, have you looked there for any answers?

[https://help.ubuntu.com/](https://help.ubuntu.com/)
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

> - so can you help me out with a system analysis tool?
Searching for 'hardware information' in the Software Centre brings up several good results.

---

### Post by Zill on 2013-01-12
> **longbeard said:**
> ...Just want to know what harware is installed on my device...
To produce a listing of your hardware open a terminal (Ctrl-Alt-t) and run the following command:
```
sudo lshw -html > ~/Desktop/hardware.html
```
Click on the resulting file on your Desktop (hardware.html) to open this in your web browser.

---

### Post by offgridguy on 2013-01-12
Some helpful suggestions, thanks.

---

### Post by claracc on 2013-01-13
If you have fixed your problem, please, mark the thread as solved with thread tools.

---

### Post by longbeard on 2013-01-13
Thank you everyone, you saved my day ..! :)

All very good answers! lshw is the one that rocks. I don't so much recommend lspci as it only brings a list of cards and controllers. Sysinfo is nice for a start but needs amplification.

Even a non-geek technician from time to time wants to know what memory chips or storage devices he has installed. I recommend Ubuntu should offer an easy accessible and detailed (down to manufacturer and organisation) hardware surview as a standard. Sooner or later everyone needs it. Thank you for your attention! 
):P

---

### Post by Zill on 2013-01-13
> **longbeard said:**
> ...I recommend Ubuntu should offer an easy accessible and detailed (down to manufacturer and organisation) hardware surview as a standard...
Err... lshw (list hardware) *is* a Linux standard. ;-)

---

### Post by Cheesemill on 2013-01-13
> **longbeard said:**
> lshw is the one that rocks. I don't so much recommend lspci as it only brings a list of cards and controllers.

Quite a few interesting commands begin with ls, here's a brief run-down...

lshw - **l**i**s**t **h**ard**w**are
lspci - **l**i**s**t **pci** devices
lsusb - **l**i**s**t **usb** devices
lsblk - **l**i**s**t **bl**oc**k** devices (drives)

---

