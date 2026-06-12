---
title: "No Such File"
date: 2024-05-26
forum: General Help
---

### Post by daniell59 on 2024-05-26
What am my missing. Can somebody please tell me why the terminal says no such file when I can see it.

daniel@daniel-N68SA-M2S:~$ cd Downloads
daniel@daniel-N68SA-M2S:~/Downloads$ sudo su
[sudo] password for daniel: 
root@daniel-N68SA-M2S:/home/daniel/Downloads# ls
brscan3-0.2.13-1.amd64.deb  linux-brprinter-installer-2.2.3-1  thunderbird.tmp
root@daniel-N68SA-M2S:/home/daniel/Downloads# gunzip linux-brprinter-installer-2.2.3-1.gz
gzip: linux-brprinter-installer-2.2.3-1.gz: No such file or directory
root@daniel-N68SA-M2S:/home/daniel/Downloads# 

Thanks

---

### Post by daniell59 on 2024-05-26
I am trying to install drivers for my MFC-7340. I was able to install printer drivers but I am really having difficulty installing scanner drivers.

[https://support.brother.com/g/b/downloadhowto.aspx?c=us&lang=en&prod=mfc7340_us_as&os=128&dlid=dlf006642_000&flang=4&type3=566](https://support.brother.com/g/b/downloadhowto.aspx?c=us&lang=en&prod=mfc7340_us_as&os=128&dlid=dlf006642_000&flang=4&type3=566)

Thanks

---

### Post by ActionParsnip on 2024-05-26
There is no "brprinter-installer-2.2.3-1.gz" in that directory. Read your ls output....

---

### Post by daniell59 on 2024-05-26
> **ActionParsnip said:**
> There is no "brprinter-installer-2.2.3-1.gz" in that directory. Read your ls output....

I got past that. I am now having immense trouble understanding how to install the drivers for the scanner part.

---

### Post by ActionParsnip on 2024-05-26
```

sudo apt install /home/daniel/Downloads/brscan3-0.2.13-1.amd64.deb
sudo apt -f install

```
Should do it

---

### Post by ActionParsnip on 2024-05-26
If it doesn't install then use the "force" command on the site but use the same filename I gave earlier

---

### Post by daniell59 on 2024-05-26
> **ActionParsnip said:**
> If it doesn't install then use the "force" command on the site but use the same filename I gave earlier

Some things installed but the scanner is not detected.
Please elaborate about using the force command.

---

### Post by currentshaft on 2024-05-26
sl

---

### Post by daniell59 on 2024-05-26
> **currentshaft said:**
> This should work instead of messing with random packages from random websites as root:

sudo apt install printer-driver-brlaser
Thanks, but the scanner was not detected.


daniel@daniel-N68SA-M2S:~$  sudo apt install printer-driver-brlaser 
[sudo] password for daniel: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
printer-driver-brlaser is already the newest version (6-3build2).
printer-driver-brlaser set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
daniel@daniel-N68SA-M2S:~$

---

### Post by currentshaft on 2024-05-26
si

---

### Post by daniell59 on 2024-05-26
> **currentshaft said:**
> Interesting. Does it show up in the outputs of "sudo dmesg" or "lspci"?

No mention of it.

---

### Post by currentshaft on 2024-05-27
al

---

### Post by daniell59 on 2024-05-27
> **currentshaft said:**
> Any way you could try the device with another USB cable or computer?

A thought just came to me. Previously I had no trouble when I was using Ubuntu 22.04. The problem started with Ubuntu 24.04. Soon I will install Ubuntu 22.04 on another drive and see what happens.

---

### Post by daniell59 on 2024-05-28
I tried to get the scanner work in Ubuntu 22.04. The installation went smooth but only the printer part would work. Since it once worked, I don't know why it won't work again.

MFC-7340

---

### Post by dragonfly41 on 2024-05-28
You could try installing a Windows VM in Ubuntu and install there ..

Inconvenient I know but Windows seems to have more coverage.
That is what I have to do for my very old Canon scanner which does not function in Ubuntu.

---

### Post by daniell59 on 2024-05-28
> **dragonfly41 said:**
> You could try installing a Windows VM in Ubuntu and install there ..

Inconvenient I know but Windows seems to have more coverage.
That is what I have to do for my very old Canon scanner which does not function in Ubuntu.
The scanner is detected in Windows. This is the problem. Brother does not offer OCR software for Windows 10.
Also, I am now unable to install my old Epson scanner in Linux.

---

### Post by TheFu on 2024-05-28
I run **bscan** manually when I want to scan with my old Brother MFC.  Then I use **gscantopdf** (or gscan2pdf?) to scan, clean up the image, then OCR it.  Depending on the type of document, the OCR might be 50% - 90% accurate.  For me, the OCR is only for finding the document later though Recoll (a google-like local search tool) for local storage.

Once bscan has been started the buttons on the front of the MFC work to set color/gray levels and the page feeder works as expected for multi-page scans.

My next scanner/fax will be another Brother, but not require any computer to scan or fax. If it comes with a printer, that printer will never be used again after the ink is empty or dried out.  Ink prices are higher than what the same amount of platinum costs. Crazy.  I have a laser printer for printing for less than $0.01 per page, not $0.20-$1.00 per page.  For scanning, I expect the MFC to write the images to an SD, MicroSD, or USB flash drive.  My current MFC has those ports, but only for printing specific document types, which I've never attempted to use.  Getting printing working has been nearly automatic since 16.04 provided avahi and cups are installed.  Looking at the printer config tool, if the printer is on, it will magically show up in the dialog and be available on the network.  My MFC is USB-only, no networking at all.

There are some 10 yr old standards - Driverless Printing and Driverless Scanning which should be widely available.  Those devices use generic interfaces and don't require any drivers to be loaded.  Sometime to consider next time it is time to replace these devices.  Loading drivers to print or scan is so, so, so 2010.
[https://wiki.debian.org/CUPSDriverlessPrinting](https://wiki.debian.org/CUPSDriverlessPrinting)
[https://openprinting.github.io/gsoc2019/03-sane-module/](https://openprinting.github.io/gsoc2019/03-sane-module/)  <--- Driverless Scanning is coming. This link is for students to create a SANE driver for driverless scanning.

Only people with the exact same device will likely be able to help.  I have a Brother MFC-240C from 2008.  Every OS update to my print server means I get to relearn how to make printing and scanning work all over again.  My print server runs 20.04 Server, so I don't have any experience

---

### Post by daniell59 on 2024-05-29
I just contacted Brother by chat. They said that a Linux support team would get in touch with me and walk me through. If that is the case, I am very impressed with Brother.

---

