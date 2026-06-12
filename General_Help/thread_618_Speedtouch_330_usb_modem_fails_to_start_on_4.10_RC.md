---
title: "Speedtouch 330 usb modem fails to start on 4.10 RC"
date: 2004-10-14
forum: General Help
---

### Post by quillian on 2004-10-14
Using the source code speedtouch_1.3-1.tar.gz and following the install instructions (which includes the location of the firmware) all procedes apparently successfully.

speedtouch-start fails.

Running speedtouch-doctor.sh indicates that the failure is due to the absence of /proc/pci.

I've successfully used this source code on SuSE 8.2 &amp; Manadrake 9.2 both of which have /proc/pci.

Intrestingly the Ubuntu live cd DOES have /proc/pci.

Help will be appreciated.

---

### Post by articpenguin on 2008-03-08
try 
mkdir

---

