---
title: "[SOLVED] Sound in laptop, but not in speakers"
date: 2008-02-04
forum: General Help
---

### Post by dmf86 on 2008-02-04
Hi there. I have Ubuntu 7.10 installed in a Toshiba A200-1QK, with an onboard sound card. My problem is that, i have sound in my laptop speakers, but i have others speakers connected to the headphones jack (which worked perfectly in windows), and now, i got no sound coming from them. Any ideas? Thanks.

---

### Post by ugm6hr on 2008-02-04
> **dmf86 said:**
> Hi there. I have Ubuntu 7.10 installed in a Toshiba A200-1QK, with an onboard sound card. My problem is that, i have sound in my laptop speakers, but i have others speakers connected to the headphones jack (which worked perfectly in windows), and now, i got no sound coming from them. Any ideas? Thanks.

Have you looked at your alsamixer settings:
[http://ubuntuforums.org/showpost.php?p=2763743&postcount=9](http://ubuntuforums.org/showpost.php?p=2763743&postcount=9)

---

### Post by dmf86 on 2008-02-04
Hum, yes, it's all unmuted... any more?

---

### Post by ugm6hr on 2008-02-04
> **dmf86 said:**
> Hum, yes, it's all unmuted... any more?

& maximized?  Use up arrow.

I have heard that some sound cards don't have enough alsamixer channels though...

---

### Post by dmf86 on 2008-02-25
Yes, all unmuted and all up... don't know what else to do. :\

---

### Post by fs3rp4 on 2008-02-25
I had this problem in my laptop and the only solution was download the latest alsa drivers and libs and compile:

[ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.16.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.16.tar.bz2)
[ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.16.tar.bz2](ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.16.tar.bz2)
[ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.16.tar.bz2](ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.16.tar.bz2)

---

### Post by dmf86 on 2008-03-11
Well, after upgrading to Hardy Alpha 6 the problem is solved. :D

---

