---
title: "No Audio - Intel 6 series/c200"
date: 2013-02-11
forum: General Help
---

### Post by Cpierce on 2013-02-11
I have a dell inspiron N4110 with an Intel 6 series/c200 high definition audio controller. I installed Ubuntu 12.04 and have no sound from speakers or headphones. Mircophone doesn't work either. This is a common computer, but google didn't show any solutions that I could find. I am not sure what all commands I need to run to help solve the problem, but here is a couple of outputs to get started:

lspci -nn | grep '\[04[80][13]\]'

00:1b.0 Audio device [0403]: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller [8086:1c20] (rev 05)


aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC269VB Analog [ALC269VB Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


It appears that it is seeing the card, but it is not loading the correct driver module. I haven't checked the HDMI yet. Thought I would get the rest of the sound working first.

If anyone can help, I sure would appreciate it

---

### Post by Yellow Pasque on 2013-02-11
> It appears that it is seeing the card, but it is not loading the correct driver module.
I'm not sure why you would say that. If snd-hda-intel wasn't loaded, you wouldn't have output for aplay -l.
Anyway.. the first thing I would try is using latest driver: [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)
If that doesn't work, give alsa info: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by Cpierce on 2013-02-12
Thank you very much for your reply. As you saw in my first post, I don't have a clue how to fix sound.

I downloaded the deb package and installed it, followed by the terminal command and reboot. But I still have no sound or microphone. I uploaded the info to alsa which can be found here:

[http://www.alsa-project.org/db/?f=dfb2d328bd7c8bab45cad2589becfcfefe76eb9a](http://www.alsa-project.org/db/?f=dfb2d328bd7c8bab45cad2589becfcfefe76eb9a)

I thank you for helping me out.

---

### Post by Cpierce on 2013-02-12
Here is a picture of alsamixer:

---

### Post by Yellow Pasque on 2013-02-12
Are you sure you got the right .deb package? Your ALSA info still says Driver=1.0.24, when it should be 1.0.25 after installing the alsa/dkms .deb

---

### Post by Cpierce on 2013-02-12
From the link you gave me, I installed the third one down which is:

dkms-hda - 0.201302121940~precise1

I can try to install again. It appeared to install correctly with software center. I have a normal installation of Ubuntu 12.04 i386, so I didn't think I should install "dkms-hda-lts-quantal - 0.201302121943~precise1" which is the other precise package. 

I will install again and report back.

Again, thank you

---

### Post by Cpierce on 2013-02-13
I reinstalled again only using gdeb instead of software center. gdeb said the package was installed, but I went ahead and installed again. After that I ran the terminal command and rebooted. Still no sound. I ran another alsa report which can be found here:

[http://www.alsa-project.org/db/?f=cdf30ec7b86e3bbacf74f377ee2af922345ca41a](http://www.alsa-project.org/db/?f=cdf30ec7b86e3bbacf74f377ee2af922345ca41a)

---

### Post by Yellow Pasque on 2013-02-13
For whatever reason, the alsa-dkms package doesn't seem to be taking effect. The next thing I would try is a newer kernel (either using the 3.5 backport from the precise repo or using a LiveUSB of 'buntu 12.10).

---

### Post by Cpierce on 2013-02-13
Not sure how to do that. I wanted to stay with the LTS version, but do you think the new Ubuntu 13 would fix this ? It would be worth trying the liveCD of Ubuntu 13. 

But if I stayed with the LTS, how would I install the backports that you are referring to ?

---

### Post by Cpierce on 2013-02-14
I booted up on the liveCD for both 12.10 and 13.04. Sound did not work for either out of the box. 

I love Ubuntu and really want to get this fixed.

---

### Post by Yellow Pasque on 2013-02-14
The next step is filing a bug. If possible and not too inconvenient, use the Ubuntu 12.10 LiveCD to do so (ubuntu-bug is the command). Also, note that you have tested Ubuntu 13.04 in your report.

---

### Post by Cpierce on 2013-02-14
So we are at a stand-still now ?

---

### Post by jocheem67 on 2013-02-14
Did you check alsamixer ?

In terminal just type alsamixer...look for muted channels, the ones with 'mm'  > unmute them with "m" 

It apppears to me that a new alsaversion is not  necessary..

---

### Post by Cpierce on 2013-02-15
I did check Alsamixer, although I don't know much about it. I posted a picture of my alsamixer in #4 on the first page. Nothing appears to be muted, but the volumes are down and can't be adjusted.

---

### Post by jocheem67 on 2013-02-16
Did you use the arrowkeys ?

And btw possibly a solution lies in editing /etc/modprobe.d/alsa-base.conf. See this thread and the example there:

[http://ubuntuforums.org/showthread.php?t=2058548](http://ubuntuforums.org/showthread.php?t=2058548)

---

### Post by Cpierce on 2013-02-16
First, Thank you for your reply !

I did try to use the arrow keys in alsamixer. And I will try the fix in your link. Most of the fixes I have read and tried have been adding a line to alsa.conf, but this one deals with deleting "rtc". I will try this and report back.

Thanks again

---

### Post by Cpierce on 2013-02-16
I went into my /etc/modules and I don't have a "rtc" to delete. Here it is :

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp






Here is my  /etc/modprobe.d/alsa-base.conf :

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

### Post by Cpierce on 2013-02-21
bump

---

