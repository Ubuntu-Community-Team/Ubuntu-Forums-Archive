---
title: "HP OfficeJet Pro 8710"
date: 2016-07-26
forum: General Help
---

### Post by yinzpitmaster on 2016-07-26
I am running 16.04 with latests updates.

Purchased a new printer (HP OfficeJet Pro 8710) and wanted to connect it via ethernet. When I installed the printer the scan function would not work. (scanner not found). I downloaded the latest HPLIP from the HP site and installed. Opted to add libraries. When I tried to run HPLIP it could not find the printer. I could connect to it via "Settings->Printers" but not scan or obtain printer info. Thought about removing ALL HP drivers and CUPS and starting over. Just not sure how or if I should.

What can I do to correct this issue?

---

### Post by yinzpitmaster on 2016-07-30
Any suggestions for the post? Still can't find scanner but can print.

---

### Post by QDR06VV9 on 2016-07-30
What dose this report...paste back the output.
```
apt-cache policy libsane-hpaio sane-utils
```

---

### Post by pqwoerituytrueiwoq on 2016-07-30
i have not tried to access a scanner directly via Ethernet but if it works like a shared usb scanner on linux you need to put the ip address of the printer in here
/etc/sane.d/net.conf

worst case scenario you can use a raspberry pi to share the scanner
scanner -> usb -> pi -> Ethernet -> router -> Ethernet -> desktop

---

### Post by yinzpitmaster on 2016-11-15
libsane-hpaio:
  Installed: 3.16.7+repack0-1ubuntu1
  Candidate: 3.16.7+repack0-1ubuntu1
  Version table:
 *** 3.16.7+repack0-1ubuntu1 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) yakkety/main amd64 Packages
        100 /var/lib/dpkg/status
sane-utils:
  Installed: 1.0.25+git20150528-1ubuntu2
  Candidate: 1.0.25+git20150528-1ubuntu2
  Version table:
 *** 1.0.25+git20150528-1ubuntu2 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) yakkety/main amd64 Packages
        100 /var/lib/dpkg/status

---

### Post by jayaalathara on 2017-02-12
> **yinzpitmaster said:**
> I am running 16.04 with latests updates.

Purchased a new printer ([[COLOR=#000000]HP OfficeJet Pro 8710[/COLOR]]("https://www.printerdriverforwindows.com/hp-officejet-pro-8710-all-in-one-printer-driver-download")) and wanted to connect it via ethernet. When I installed the printer the scan function would not work. (scanner not found). I downloaded the latest HPLIP from the HP site and installed. Opted to add libraries. When I tried to run HPLIP it could not find the printer. I could connect to it via "Settings->Printers" but not scan or obtain printer info. Thought about removing ALL HP drivers and CUPS and starting over. Just not sure how or if I should.

What can I do to correct this issue?

after updating to Ubuntu 16.10 some how i got this working

---

