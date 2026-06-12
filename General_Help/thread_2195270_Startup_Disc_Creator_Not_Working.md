---
title: "Startup Disc Creator Not Working"
date: 2013-12-23
forum: General Help
---

### Post by daniell59 on 2013-12-23
I tried to put Porteus on a USB Drive using the Startup Disc Creator. The necessary boxes were greyed out. Any assistance will be appreciated. Ubuntu 12.04 64

---

### Post by sammiev on 2013-12-23
I use [unetbootin]("http://unetbootin.sourceforge.net/"), it should be in the software center.

---

### Post by daniell59 on 2013-12-23
I just downloaded UNetbootin. I am trying to figure out how to manually select files. Assistance will be appreciated.

---

### Post by nerdtron on 2013-12-23
You mean select the correct ISO file? [http://www.mytechguide.org/7818/create-linux-live-bootable-usb-stick-using-unetbootin/](http://www.mytechguide.org/7818/create-linux-live-bootable-usb-stick-using-unetbootin/)

---

### Post by sammiev on 2013-12-23
> **daniell59 said:**
> I just downloaded UNetbootin. I am trying to figure out how to manually select files. Assistance will be appreciated.

Download the ISO onto your computer. ( usually in Downloads ) Start Unetbootin and browses for the ISO you are looking for in Downloads. Select and burn to the USB.

---

### Post by Vormeph on 2013-12-23
You could always use the command line method, but I found that it screws up your USB insofar that gParted/startup disk creator won't even recognise it. Do this only as a last resort:

```
dd bs=3M if={INSERT PATH TO ISO HERE} of={INSERT LOCATION OF USB HERE} && sync
```

e.g. ```
dd bs=3M if=~/Downloads/ubuntu.iso of=/dev/sdb && sync
```

Do not append sdb1 or sdc2 or whatever partition: just the drive.

Good luck!

I have not used Porteous so I'm not sure if this method would work, but it has for me on other iso files.

---

### Post by ajgreeny on 2013-12-23
Startup-disc-creator is only meant for, and only works with ubuntu, or ubuntu based ISO files, though it will work with Mint and Bodhi, I think, but certainly not all ISOs from third party OSs.

I do not know Porteus, but that may be the problem with SDC not working for you.

---

