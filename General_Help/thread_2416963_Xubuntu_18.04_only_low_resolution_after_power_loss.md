---
title: "Xubuntu 18.04 only low resolution after power loss"
date: 2019-04-18
forum: General Help
---

### Post by twgray on 2019-04-18
After a power surge XFCE only boots to 1024x768 res display. Have tried re-installing nvidia 390 drivers to no avail. Help please!

---

### Post by #&amp;thj^% on 2019-04-18
Can you tell us how the Driver was installed?

---

### Post by oldrocker99 on 2019-04-18
IF you download the nVidia drivers from nVidia's own website, you're likely to come to grief. If you installed the driver *this* way,
```
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt update
sudo apt install nvidia-390
```

Then your problem is something else.

---

### Post by twgray on 2019-04-18
The original driver was installed with 18.04 upgraded and worked perfectly until power outage.  I reinstalled with synaptic.  I couldn't install the driver downloaded from the Invidia site due to an error with it being unable to open nurses 6 desktop.

---

### Post by #&amp;thj^% on 2019-04-18
Well the only thing I can add is give this a try:
```
sudo apt remove --purge nvidia*
```
Now sometimes it would be better to completely power down the machine before trying a new install.
To re-install use the code oldrocker99 has offered:
```
sudo apt install nvidia-390
```
And Good Luck.

---

### Post by deadflowr on 2019-04-18
Run a file system check.
A power surge might have corrupted the file system.

---

### Post by twgray on 2019-04-19
The problem turned out to be UEFI Windows mode became selected as a result of the power surge/outage.  Turning this off solved the problem.

---

