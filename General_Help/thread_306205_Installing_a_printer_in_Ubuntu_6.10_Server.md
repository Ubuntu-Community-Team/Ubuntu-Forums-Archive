---
title: "Installing a printer in Ubuntu 6.10 Server"
date: 2006-11-24
forum: General Help
---

### Post by SiR GadaBout on 2006-11-24
Hi,

I have a Samsung ML-4500 parallel printer that comes with rpm drivers for x86.  Can someone advise me how to go about installing this printer using the CLI in Edgy Eft Server?  No documentation seems to exist for this, and every search only brings up solutions for GUI users.  I'm a CUPS newbie so explicit instructions would be preferred.

Thanks,

SiR G.

---

### Post by makadam on 2006-11-30
Hello

Have a look at: [http://www.cups.org](http://www.cups.org).

---

### Post by SiR GadaBout on 2006-12-03
Hi Makadam,

I had already tried cups.org, but at your prompting I went back.  Turns out the lack of documentation I was experiencing was both correct and incorrect - there is no specific user manual for CUPS 1.2.  However, that's because the manuals for 1.1 are still valid.  Now that I've downloaded these I've made some headway though, as a newbie always finds, I've come up against another brick wall (subjectively-speaking).  I've used lpadmin to create a new printer, and have downloaded an appropriate PPD.  However, I still get this error message:

job-sheets=none,none printer-info=laserjet printer-is-accepting-jobs=1 printer-is-shared=1 printer-make-and-model='Samsung ML-4500 Foomatic/gdi (recommended)' printer-state=5 printer-state-change-time=1165183852 printer-state-reasons=cups-missing-filter-error printer-type=135172

I'm trying to print a PDF file, which I thought would be converted by CUPS automatically.  Appears I was wrong.  Any thoughts?  There is a Samsung-provided rpm for this printer, but all the installation info is for GUI users.  I know I'll have to use 'alien' to convert this file, but what then?
Feeling lost,
SiR G.

---

### Post by makadam on 2006-12-12
Hello SiR GadaBout

First convert the RPM package using alien:
1. Convert RPM to DEB or TGZ.
```
sudo alien -d pkgname.rpm
```
```
sudo alien -t pkgname.rpm
```
2. Try to install the deb packege
```
dpkg -i pkgname.deb
```
If this does not work extract the TGZ file to copy the print driver to the right place.
```
sudo tar xvzf pkgname.tgz -C /
```
3. Reload the driver using
```
sudo ldconfig
```
4. Check if your printers PPD file is not ziped.
```
cd /usr/share/cups/model
```.
Unzipp the files if needed.
```
sudo gunzip pkgname.ppd.gz
```
5. Restart CUPS
```
sudo /etc/init.d/cupsys restart
```
6. If everything works well, you can install your printer using this driver. Try to follow the CUPS manual or use a client which connects using a Internet browser to your print server.

I hope this helps you at least to install the driver.

Makadam

---

### Post by Lucho77 on 2006-12-14
> **SiR GadaBout said:**
> Hi,

I have a Samsung ML-4500 parallel printer that comes with rpm drivers for x86.  Can someone advise me how to go about installing this printer using the CLI in Edgy Eft Server?  No documentation seems to exist for this, and every search only brings up solutions for GUI users.  I'm a CUPS newbie so explicit instructions would be preferred.

Thanks,

SiR G.

May be this link could help you, it did to me; [http://www.ubuntuforums.org/showthread.php?t=240282&highlight=cups](http://www.ubuntuforums.org/showthread.php?t=240282&highlight=cups)

---

