---
title: "Scanner accessible only by root"
date: 2008-05-14
forum: General Help
---

### Post by roy.nico on 2008-05-14
Hi everybody.

I have a Ubuntu Hardy, a scanner Agfa Snapscan 1212 usb and the  programs sane, xsane, etc.. are intalled.
It functions well if i launch xsane as root. But, if i launch 
xsane as a normal user, i get the message : (i translate from the french) "Looking for hardware ... no hardware found".
It must be a stupid problem of permissions... Nevertheless, the user IS in the group scanner.
* Following the tutorial [HTML]ubuntu http://doc.ubuntu-fr.org/scanner_acer_benq[/HTML], i installed the firmware SnapScann1212U.bin in  /etc/sane.d for which i set the access rights open for reading and executing for eerybody (just in case...)
* From a normal account, i have :
```

sane-find-scanner
found USB scanner (vendor=0x06bd, product=0x2061) at libusb:001:003

```
* From root i have :

```
sudo sane-find-scanner
found USB scanner (vendor=0x06bd [AGFA], product=0x2061 [ Snapscan1212u_2]) at libusb:001:003

```

... which seems to be somehow more complete ...

Thanks a lot in advance for any idea.

nico

---

