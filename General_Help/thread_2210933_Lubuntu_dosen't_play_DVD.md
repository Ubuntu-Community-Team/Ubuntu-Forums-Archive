---
title: "Lubuntu dosen't play DVD"
date: 2014-03-13
forum: General Help
---

### Post by R4m4m on 2014-03-13
I just installed Lubuntu 13.10 and it dosen't play DVD's. I installed vlc and css and I get a notice saying  "Couldn't open DVD device /dev/dvd (No such file or directory). I used to be able to play dvd's when I could install libdvdcss2 from medibuntu but now I have a problem.

---

### Post by Elfy on 2014-03-13
*Thread moved to **General Help**.*

You can get libdvdcss2 by using repository from videolan

[http://www.videolan.org/developers/libdvdcss.html](http://www.videolan.org/developers/libdvdcss.html)

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by matt_symes on 2014-03-13
Hi

/dev/dvd has been depricated.

From Martin Pitt (#5) of this thread

[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/926976](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/926976)

> 
No, they weren't forgotten. Upstream dropped the /dev/cdrom and  /dev/dvd* symlinks long ago, we just carried them a little longer. This  concept of static symlinks has shown to be unreliable with hardware  changes (as you noticed yourself when changing the SCSI drive), and  modern desktops and CD handling software should not assume any of these  links any more but instead ask sysfs or libudev about available CD  drives and their capabilities.

What version of vlc are you using ? maybe upgrade it ?

You could create the link yourself.

Kind regards

---

### Post by ajgreeny on 2014-03-13
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs) tells you how to deal with libdvdcss now that medibuntu has gone.

The script provided by libdvdread4 has been updated to get libdvdcss2 from videolan direct.

---

### Post by oldos2er on 2014-03-13
> **R4m4m said:**
> I just installed Lubuntu 13.10 and it dosen't play DVD's. I installed vlc and css and I get a notice saying  "Couldn't open DVD device /dev/dvd (No such file or directory). I used to be able to play dvd's when I could install libdvdcss2 from medibuntu but now I have a problem.

Once you have libdvdcss2 installed, choose /dev/sr0 in vlc.

---

