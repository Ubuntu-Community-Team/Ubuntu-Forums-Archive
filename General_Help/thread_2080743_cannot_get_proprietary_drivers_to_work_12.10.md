---
title: "cannot get proprietary drivers to work 12.10"
date: 2012-11-04
forum: General Help
---

### Post by Darth Poder on 2012-11-04
ever since I upgraded to Ubuntu 12.10 I cannot get my ATI graphic drivers on my laptop. I'm running a ATI HD Radion 4200 Model series so there should be plenty of support. When ever I try to install them with Ubuntu software center I get problem that I don't really wont to discuss, being that I've already discussed them in another thread. Now when I try to install them using the downloaded file form the AMD website it get this little message, please check In the attachments for this thread.

can anyone help me.

---

### Post by Yellow Pasque on 2012-11-04
It's not going to work (AMD dropped support for RadeonHD 2000-4000 in fglrx/Catalyst). Use the open-source driver. [https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1058040](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1058040)

---

### Post by Mark Phelps on 2012-11-05
To add more info ... 12.10 brings another version of the X-server (1.13) and evidently, AMD has decided NOT to upgrade their Linux drivers for the HD 2x/3x/4x line to work with that X-Server.

So, as mentioned, there will be no new Linux drivers from AMD for these chipsets.

---

### Post by dr_saaron on 2012-11-05
I was able to follow the suggestion at [http://www.unixmen.com/ubuntu-12-10-and-amd-catalyst-problem-solved/](http://www.unixmen.com/ubuntu-12-10-and-amd-catalyst-problem-solved/) to get the video driver working again.

---

### Post by Mark Phelps on 2012-11-05
> **dr_saaron said:**
> I was able to follow the suggestion at [http://www.unixmen.com/ubuntu-12-10-and-amd-catalyst-problem-solved/](http://www.unixmen.com/ubuntu-12-10-and-amd-catalyst-problem-solved/) to get the video driver working again.

Saw something similar posted from another site (ppa) -- but in their case, the script downgraded the X-server to v1.12.  My concern with that, is unless that package was then held back, the next routine upgrade that replaces that with X-server 1.13 will render the display useless.

---

