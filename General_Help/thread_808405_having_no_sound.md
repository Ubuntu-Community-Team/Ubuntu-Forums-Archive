---
title: "having no sound"
date: 2008-05-26
forum: General Help
---

### Post by damansandhu on 2008-05-26
hi , i am using ubuntu 8.04 and i have installed all the essential codecs but i am getting no sound from audio and video files , audio and video files keeps on playing without sound , but in youtube i can hear sound from videos.

i am using creative sb audigy value 7.1

---

### Post by TeoBigusGeekus on 2008-05-26
Did you install ubuntu-restricted-extras?

---

### Post by ~Nightingale~ on 2008-05-26
yarg same problem

---

### Post by damansandhu on 2008-05-27
still no sound after installing ubuntu-restricted-extras
 what to do now???

---

### Post by RheaHS on 2008-05-27
same problem here, with an onboard sound. Just getting specs.

---

### Post by damansandhu on 2008-05-27
my sound use to work absolutely fine with ubuntu 7.04 fiesty , i dont know what is wrong ubuntu 8.04

---

### Post by damansandhu on 2008-05-27
helpp plzz

---

### Post by danwood76 on 2008-05-27
What software are you using to play the audio/video?

Have you tried to play files whilst no other apps are running? (Like closing firefox etc)

---

### Post by TeoBigusGeekus on 2008-05-27
Post us the output of
```
lspci
```
to see the sound card you're using.

---

### Post by damansandhu on 2008-05-27
yes i have tried but still it didn't works :((


daman@ULTIMATE:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:07.0 Multimedia audio controller: Creative Labs SB Audigy LS
02:00.0 VGA compatible controller: nVidia Corporation Geforce 9600 GT 512mb (rev a1)
daman@ULTIMATE:~$

---

### Post by TeoBigusGeekus on 2008-05-27
[http://ubuntuforums.org/showthread.php?t=546931]("http://ubuntuforums.org/showthread.php?t=546931")

I hope that helps you...

---

### Post by damansandhu on 2008-05-27
it didn't helped me because i am using creative sound card :(

---

### Post by TeoBigusGeekus on 2008-05-27
Oh sorry!!! I didn't see it down there...

---

### Post by damansandhu on 2008-05-27
so any suggestions??

---

### Post by damansandhu on 2008-05-27
helpp plzz

---

### Post by damansandhu on 2008-05-27
somebody please help me as sound is very essential part of os

---

### Post by TeoBigusGeekus on 2008-05-27
What about this?
[http://ubuntuforums.org/showthread.php?t=564972&highlight=Creative+Labs+SB+Audigy+LS]("http://ubuntuforums.org/showthread.php?t=564972&highlight=Creative+Labs+SB+Audigy+LS")

---

### Post by damansandhu on 2008-05-27
i am using creative sound blaster audigy 7.1 value and i can hear sound from youtube videos but not from audio and video files of my pc :(

---

### Post by danwood76 on 2008-05-27
I think it may have something to do with the priority of your sound cards as you have onboard sound aswell.
YOu can tell it to prioritize the audigy by adding a couple of lines to the bottom of your /etc/modprobe.d/alsa-base file.

So open the file for writing:
```

sudo gedit /etc/modprobe.d/alsa-base

```
add these lines to the bottom:
```

options snd-ca0106  index=0
options snd_hda_intel index=1

```
I'm pretty sure the driver your audigy uses is the ca0106, but im not 100%. And also I'm pretty sure your nvidia onboard uses the hda_intel driver but again not 100% sure.

After you've made those changes reboot and see if its made a difference.
Check in System -> Preferences -> Sound and run the sound tests to see if you get tone out. (try selecting different sound cards also within this)

To be honest creative soundcards are poor quality and offer no real advantage over onboard sound.
Especially if your just gaming or watching videos, and if you were doing audio work then there are far better sound cards available for very modest amounts of cash.

---

### Post by damansandhu on 2008-05-27
i think you are right , there is sound coming out from onboard jacks but volume level is too low

---

### Post by damansandhu on 2008-05-27
hey i added these two lines , but still nothing happened , you can see


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
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
options snd-ca0106  index=0
options snd_hda_intel index=1

---

### Post by damansandhu on 2008-05-27
i have amd processor with onboard realtek sound manager and it sounds very bad thats why i bought this audigy sound card which sounds many times better than my onboard.

---

### Post by danwood76 on 2008-05-27
can you post the output of this command please:
```

cat /proc/asound/cards

```
I may have just got the drivers wrong.

-- edit --

This one is actually better for the job:
```

grep 'snd*' /proc/asound/modules

```

---

### Post by damansandhu on 2008-05-27
daman@ULTIMATE:~$ cat /proc/asound/cards
 0 [CA0106         ]: CA0106 - CA0106
                      Audigy SE [SB0570] at 0xcc00 irq 20
 1 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfe028000 irq 16
daman@ULTIMATE:~$ 




i dont know that is problem , youtube sounds load and clear.

---

### Post by damansandhu on 2008-05-27
daman@ULTIMATE:~$ grep 'snd*' /proc/asound/modules
 0 snd_ca0106
 1 snd_hda_intel
daman@ULTIMATE:~$

---

### Post by danwood76 on 2008-05-27
What you might be able to do is disable the onboard sound in your BIOS, this would stop it from loading the onboard sound at all.

Have you made sure you have all the volume sliders up in the volume controls?

---

### Post by damansandhu on 2008-05-27
thanks man , my problem is solved by disabling onboard in bios ,

can you tell me cool audio players?

---

### Post by yaknowwat on 2008-05-27
Personally i would suggest banshee's latest beta's you have to add a repository first to get  the latest beta's easily.

[http://www.ubuntu-unleashed.com/2008/05/banshee-is-10-beta-1-released-with-ppa.html](http://www.ubuntu-unleashed.com/2008/05/banshee-is-10-beta-1-released-with-ppa.html)

latest is beta 2

Exaile is decent but the interface to me personally wasn't all that nice. and when i went to remove music from the library it immediately asked me if i wanted to remove them from the hard drive, all it took was an instant reflex and i ended up deleteing a load of music... I personally think the default settings should not prompt for deleting a song from the drive but just removing from the playlist.

---

