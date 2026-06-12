---
title: "Wrecked my Alsa 1.0.15 Kubuntu Acer Aspire 5720"
date: 2007-11-25
forum: General Help
---

### Post by wfmk on 2007-11-25
Hello

I have just installed Kubuntu on my Acer Aspire 5720.

I followed the instructions for upgrading Alsa to 1.0.15 as on 

[http://www.antonywilliams.com/2007/10/bash-script-to-automate-compiling-alsa.html](http://www.antonywilliams.com/2007/10/bash-script-to-automate-compiling-alsa.html)

and everything worked smoothly.

Then I added 'options snd-hda-intel model=acer' to my alsa which now reads as:


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
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
options snd-hda-intel model=acer


I had done this successfully with Ubuntu a few weeks ago, but I still get no sound.

SO then I tried this method:
[https://wiki.ubuntu.com/LaptopTestingTeam/AcerAspire5720](https://wiki.ubuntu.com/LaptopTestingTeam/AcerAspire5720)

And no my sound mixer cannot be found at all. 

I must have completely knackered it :((((

Can anyone suggest a fix??

Thanks for taking the time to read this.

Martin

---

### Post by wfmk on 2007-11-26
bump! can anyone help? :(

---

### Post by Lumo on 2007-11-27
What happens if you start from the begining of the instructions here?

[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

That worked on my 5720

---

### Post by DakoCwerf on 2007-12-07
had same issue and solved it 2 days ago. (aspire 5720, fresh gutsy ubuntu 7.10)

first - i upgraded to alsa 15:
download and install alsa-driver, alsa-lib, alsa-util
when you will install driver - configure it with hda-intel card.
> 
cd alsa-driver-1.0.15
./configure --with-cards=hda-intel
make
sudo make install

next - here is a trick :) - i did upgrade for backports-modules
> sudo aptitude install linux-backports-modules-generic

last step - edit your modprobe - add 1 line at the end
> sudo gedit /etc/modprobe.d/alsa-base
add this line:
> options snd-hda-intel model=acer

then reboot - and it worked for me.
try - if it will work for you - can commit as an issue.

---

### Post by frodon on 2007-12-31
Got the exact same problem as the OP and the fix above worked nicely, thanks a lot for sharing this :)

---

