---
title: "Xsane not showing scanner"
date: 2007-05-01
forum: General Help
---

### Post by Robbyx on 2007-05-01
The visioneer Strobe xp450 scanner  is supported in the Avision Sane back end. It is showing as a device in the Device Manager, but dose not appear as a scanner option  in Xsane. My other 2 scanners are appearing in there.

Has anyone else solved this problem?

---

### Post by fanatik on 2007-05-01
try:

$ sudo scsiadd -s

to re-scan the scsi bus. you might need to install the scsi tools if not already installed....

---

### Post by Robbyx on 2007-05-01
The Visioneer stobe kp 450 is a USB device. Are the scsi tools appropriate? If so which ones should  I download?

---

### Post by rbmorse on 2007-05-01
Wadda ya get from (in a terminal window):

scanimage --l                             < that;s a lower case "L"

---

### Post by Robbyx on 2007-05-01
device `pixma:04A91706_50900F' is a CANON Canon PIXMA MP750 multi-function peripheral
device `gt68xx:libusb:001:005' is a Lexmark X73 flatbed scanner

But it is not showing the Strobe xp 450

---

### Post by Robbyx on 2007-05-02
I would very much like some suggestions as to why the USB strobe xp 450 is not showing up in xsane and yet is showing in the device manager.

---

### Post by mjmeche on 2007-05-03
[https://launchpad.net/ubuntu/+source/sane-backends/+bug/85488](https://launchpad.net/ubuntu/+source/sane-backends/+bug/85488)

Ths seems to be the problem

---

### Post by Robbyx on 2007-05-03
I wonder if the bug reported is the cause. In the link people are saying that their scanners are not creating images. However my problem is that both scan2pdf and xscan are not showing the strobe scanner as being present. I therefore can attempt to use that scanner as it is not available.

Does anyone know how to get the Strobe scanner to be recognised as being present?

---

### Post by Robbyx on 2007-05-04
Sorry to ask again but does any one have some suggestions to make xsane see the visioneer strobe scanner?

---

