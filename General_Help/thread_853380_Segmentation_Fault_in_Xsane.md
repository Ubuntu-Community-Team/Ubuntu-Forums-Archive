---
title: "Segmentation Fault in Xsane"
date: 2008-07-08
forum: General Help
---

### Post by davisch on 2008-07-08
I installed a new driver for a Samsung SCX-4500 printer/scanner that is on a windows box in my network from the mfg's disk.  Afterwards my locally connected USB Epson scanner would no longer work.  I can run Xsane from the command line with sudo so I assume the Samsung install changed a permission setting some place.  I am at a loss to know where to look.  I checked /proc/bus/usb/ but it was empty.  I have ver 8.04.

---

### Post by davisch on 2008-07-11
I found the problem.  The Samsung SCX-4500 driver install program put three files in /usr/lib/sane with the wrong permissions and owners.  Since I do not intend to use the scanner on the SCX-4500 - only the printer - I just removed the three files (libsane-smfp.so, libsane-smfp.so.1, libsane-smfp.so.1.0.1) and all is well again.  I foolishly did not use synaptic to do the install - may have saved me some grief.

---

### Post by rizox on 2011-03-16
Same here using Kubuntu 10.4. The (hell of Windows mided) installation program of the Samsung SCX-4200/4100/etc scanner-printer driver puts some files in /usr/lib/sane (libsane-smfp.so, libsane-smfp.so.1, libsane-smfp.so.1.0.1).
These files does xsane to work only as root. As non-root makes it to crash under a "Segmentation fault".
What is worse, the (hell of Windows minded) installation program of the Samsung printer/scanner does not work on its printing side with K/Ubuntu 10.4. It is made only for older versions...  :-(

---

