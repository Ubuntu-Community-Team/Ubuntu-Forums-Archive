---
title: "usb audio solved for MB n2m-e-sli"
date: 2007-08-29
forum: General Help
---

### Post by Riffer on 2007-08-29
This worked for me and I only had to edit the alsa base.

In terminal put in 

sudo nano /etc/modprobe.d/alsa-base

in that file down at the bottom is this

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2

Hash out the line "snd-usb-audio index=-2
So it looks like

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
# options snd-usb-audio index=-2
options snd-usb-usx2y index=-2


save and exit and reboot.  Thats it!!!

Hope this works for you guys,  I have sound out of rythum box etc, I don't know if it will do mics as I don't use one.  Good luck.

---

### Post by Riffer on 2007-08-31
Well I'm guessing its working for you guys asm nobody has replied that its not working :lolflag:

---

