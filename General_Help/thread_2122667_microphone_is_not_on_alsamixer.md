---
title: "microphone is not on alsamixer"
date: 2013-03-05
forum: General Help
---

### Post by freefixkorma on 2013-03-05
hello there i am running ubuntu 12.04 on a laptop hp pavilion dv4 when i have a microphone issues ,i open in terminal alsamixer and does not apear there no bars for microphone anyone with same issue please post or any help will be welcome please thanks
freefix

---

### Post by MyTinFoilHat on 2013-03-05
does "Mic" read "MM" at the very bottom of the bar?

---

### Post by freefixkorma on 2013-03-05
it reads mic jack no M

---

### Post by freefixkorma on 2013-03-05
i will post a screen shot give me a second please thanks

---

### Post by freefixkorma on 2013-03-05
[ATTACH=CONFIG]239818[/ATTACH]

---

### Post by freefixkorma on 2013-03-05
guys thanks for your help i guess is very late thanks in advance i posted screenshot of the alsamixer hope that helps if need any command line and output please let me know thanks
freefix

---

### Post by freefixkorma on 2013-03-06
hello there do you guys need aditional information please feel free i will post right away thanks}

---

### Post by xc3RnbFO8P on 2013-03-06
In alsamixer window you have to do F5 (all)
or resize window  to max

---

### Post by freefixkorma on 2013-03-06
i get this [ATTACH=CONFIG]239847[/ATTACH]

---

### Post by xc3RnbFO8P on 2013-03-06
look at the arrow on the right side, drag it to the right

---

### Post by freefixkorma on 2013-03-06
[ATTACH=CONFIG]239848[/ATTACH]

this full size thanks for reply and help 
freefix

---

### Post by xc3RnbFO8P on 2013-03-06
Show the output of:
> sudo gedit /etc/modprobe.d/alsa-base.conf

---

### Post by freefixkorma on 2013-03-06
sorry dont understand what you mean can you be more specific what to do little more detail please

---

### Post by freefixkorma on 2013-03-06
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2

---

### Post by xc3RnbFO8P on 2013-03-06
Add this line on the botton:
> options snd-hda-intel enable_msi=1options snd-hda-intel enable_msi=1
save and restart
check alsamixer

---

### Post by freefixkorma on 2013-03-06
ihave this i added the line and the alsamixer looks like this thanks for the help[ATTACH=CONFIG]239852[/ATTACH]

---

### Post by xc3RnbFO8P on 2013-03-06
Then try this: (he says it works, post #6)
[http://ubuntuforums.org/showthread.php?t=2099193]("http://ubuntuforums.org/showthread.php?t=2099193")

---

### Post by freefixkorma on 2013-03-07
i still have the same problem i followed the steps on that thread and nothing still missing the microphone on alsamixer any other ideas thanks everyone for the help i will appreciate anyone that had same issue with hp pavilion dv4 laptop thanks in advance
freefix

---

### Post by xc3RnbFO8P on 2013-03-07
Now try this:
> # Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2
[B]options snd_hda_intel model=laptop
options snd-hda-intel position_fix=1 enable=yes[/B]

---

### Post by freefixkorma on 2013-03-07
yes i was able to use the wire microphone that solve my issue but i still can use the laptop internal microphone thanks for all the time my friend this thread my help someone one day when is solve

---

