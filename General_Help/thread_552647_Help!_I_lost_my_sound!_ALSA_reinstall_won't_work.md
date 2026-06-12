---
title: "Help! I lost my sound! *ALSA reinstall won't work*"
date: 2007-09-16
forum: General Help
---

### Post by remick182 on 2007-09-16
I'm having problems understanding why my sound no longer works.  I installed Feisty a while back and got everything working with my sound card pretty much immediately, although I couldn't tell you what exactly I did step by step.  I know that it wasn't too involved, sound pretty much worked after the initial install.

Anyway, I was having problems running Return to Castle Wolfenstein using the Linux bins, and it kept crashing on a segment 11.  After looking around for a while, I dug up segment 11 being a sound related crash.  So, I went in search for a fix.  I came across PulseAudio from this[ link]("http://ubuntuforums.org/showthread.php?t=42492") which subsequently led me to the [Ubuntu:Feisty]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#Sound") page to follow " How to setup PulseAudio Sound Server".

Everything went smoothly and now RtCW loads up with no problems.  Then, I noticed that I had no sound on my system at all.  So, I went [here]("http://ubuntuforums.org/showthread.php?t=205449&highlight=pulseaudio") to try to fix ALSA and get my sound back.  After completing all of these steps, I still have no sound.  What do I do?  Is this a known bug with PulseAudio?

I don't know if my /etc/modprobe.d/alsa-base is correct or not.  I edited it like this:

> # autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --Qb snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }

# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

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
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
**options snd-hda-intel index=0**

The bold line at the end was added, I don't know if it needs to be there since I have a Toshiba A135-2386 that has an Integrated SB sound card listed as this:

dustin@toshiba-laptop:~$ cat /proc/asound/modules
 0 snd_hda_intel

---

### Post by aldeby on 2007-09-27
Your /etc/modprobe.d/alsa-base should be automatically generated,
as for this line **options snd-hda-intel index=0** I have it for my Intel ICH8 audio device, without index=0 though.

You should try running 
```
sudo alsaconf
```
and ```
depmod -a
```
after installing the drivers.

Please, concerning the use of **pulseaudio** on laptops have a look at this post too:
[http://ubuntuforums.org/showpost.php?p=3403075&postcount=10](http://ubuntuforums.org/showpost.php?p=3403075&postcount=10)

---

### Post by wrongo on 2007-09-27
[I]adamson@adamson-desktop:~$ sudo alsaconf
sudo: alsaconf: command not found[/I]

Meanwhile, I'm here because I got sick of audio troubles having two soundcards, my onboard and a CreativeLabs card. I remembered seeing a post about "two sound cards?" plus a while back some tape-transfers came out horrible, so I decided to take out the CL card and just use the on-board.

**Failed to start Volume Control: Failed to execute child process "gnome-volume-control" (No such file or directory**

Going to try the alsa reinstall...

---

