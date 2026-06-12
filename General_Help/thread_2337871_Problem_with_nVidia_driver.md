---
title: "Problem with nVidia driver"
date: 2016-09-22
forum: General Help
---

### Post by krishkat on 2016-09-22
Today I built out my AMD R7 250 graphics card and built in my new nVidia GTX 1060 graphics card. Then I removed the amd drivers and installed the nVidia drivers. But my card will not be found. I am using Ubuntu 16.04 LTS.

---

### Post by howefield on 2016-09-22
Which video drivers are you using ?

You'll probably need the nvidia drivers repository (ppa:nvidia-graphics/ppa) ?

---

### Post by krishkat on 2016-09-22
I am using nvidia x server configuration

when I start it now I get following error:
** (nvidia-settings:8437): WARNING **: PRIME: Kindprozess »/usr/bin/prime-supported« konnte nicht ausgeführt werden (Datei oder Verzeichnis nicht gefunden)
** Message: PRIME: is it supported? no


ERROR: nvidia-settings could not find the registry key file. This file should
       have been installed along with this driver at
       /usr/share/nvidia/nvidia-application-profiles-key-documentation. The
       application profiles will continue to work, but values cannot be
       prepopulated or validated, and will not be listed in the help text.
       Please see the README for possible values and descriptions.

---

### Post by Bucky Ball on 2016-09-22
> **howefield said:**
> You'll probably need the nvidia drivers repository (ppa:nvidia-graphics/ppa) ?

The drivers for that card should actually be in Additional Drivers. Others have been using the one from there. Think it's the 361 or the 367. Check Additional Drivers and you should find one with 'recommended' or 'updates' next to it. If the 367 is there, enable it.

PS: Once you have the card in, do a full 

```
sudo apt update
sudo apt full-upgrade
```

... in 16.04 then check Additional Drivers.

---

