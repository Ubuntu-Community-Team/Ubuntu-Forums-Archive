---
title: "how to check sound card"
date: 2007-04-08
forum: General Help
---

### Post by loveshocked on 2007-04-08
I am using ubuntu 6.10

usually, my sound card is functioning properly. But somehow, today, it stopped working. i can't hear any sound from my speaker while I play my mp3s.. the master volume is 100%, and i plugged it in a proper place.

i checked with windows os, and it works. I tried to play nibble, and it can't hear anything..

does any of you know how to check the functionality of my sound card in ubuntu. It stopped playing sound after i installed samba and xirc.. (does it have any corellation with it? :confused: )

---

### Post by krussell on 2007-04-08
HeLLO :-)
First of all i'd suggest to check the volume manager window (double click on the volume icon) and see whether anything is muted. Secondly, you can run 'alsamixer' in console to see the status of alsamixer.

---

### Post by loveshocked on 2007-04-08
sorry, i have checked in system. It is detected, but somehow, i can't get any sound coming from it.

---

### Post by krussell on 2007-04-08
okay...you can hear sound when logged-in as root or is it the same story?

---

### Post by Punker on 2007-04-08
> **loveshocked said:**
> I am using ubuntu 6.10

usually, my sound card is functioning properly. But somehow, today, it stopped working. i can't hear any sound from my speaker while I play my mp3s.. the master volume is 100%, and i plugged it in a proper place.

i checked with windows os, and it works. I tried to play nibble, and it can't hear anything..

does any of you know how to check the functionality of my sound card in ubuntu. It stopped playing sound after i installed samba and xirc.. (does it have any corellation with it? :confused: )

This will give you the chip set.
```

aplay -l

```

then try this 
```

sudo /sbin/modprobe snd- the chip set it gives you

```

let me know

you can also look it up here
[http://www.alsa-project.org/alsa-doc/](http://www.alsa-project.org/alsa-doc/)

---

### Post by XtremeSki2001 on 2007-04-08
I have a similar problem.

My sound had been working in Ubuntu Edgy, but now it's not.  I'm not sure where to find said volume manager, but alsamixer shows volume in each category.

Here is my output for the commands above and some additional ones while googleing.

```
erich@erich-desktop:~$ lspci
00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (rev c1)
00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev c1)
00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev c1)
00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev c1)
00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev c1)
00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev c1)
00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a4)
00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)
00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev c1)
01:07.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
01:08.0 PCI bridge: Hint Corp HB6 Universal PCI-PCI bridge (non-transparent mode) (rev 11)
02:08.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
02:09.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
03:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600/GeForce 6600 GT] (rev a2)
```

```
erich@erich-desktop:~$ amixer
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 11 [35%] [on]
  Front Right: Playback 11 [35%] [on]
Simple mixer control 'Master Mono',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 9 [29%] [off]
Simple mixer control '3D Control - Center',0
  Capabilities: volume volume-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 15
  Mono: 2 [13%]
Simple mixer control '3D Control - Depth',0
  Capabilities: volume volume-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 15
  Mono: 2 [13%]
Simple mixer control '3D Control - Switch',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 3 [10%] [off]
  Front Right: Playback 3 [10%] [off]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 3 [10%] [off]
  Front Right: Playback 3 [10%] [off]
Simple mixer control 'Surround Down Mix',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Surround Jack Mode',0
  Capabilities: enum
  Items: 'Shared' 'Independent'
  Item0: 'Shared'
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 31 [100%] [off]
Simple mixer control 'Center/LFE Down Mix',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [off]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [off] Capture [off]
  Front Right: Playback 0 [0%] [off] Capture [off]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [off] Capture [off]
  Front Right: Playback 0 [0%] [off] Capture [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [off]
  Front Left: Capture [on]
  Front Right: Capture [on]
Simple mixer control 'Mic Boost (+20dB)',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Mic Select',0
  Capabilities: enum
  Items: 'Mic1' 'Mic2'
  Item0: 'Mic1'
Simple mixer control 'Video',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [off] Capture [off]
  Front Right: Playback 0 [0%] [off] Capture [off]
Simple mixer control 'Phone',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [off]
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined cswitch cswitch-joined
  Playback channels: Mono
  Capture channels: Mono
  Mono: Playback [off] Capture [off]
Simple mixer control 'IEC958 Playback AC97-SPSA',0
  Capabilities: volume volume-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 3
  Mono: 0 [0%]
Simple mixer control 'PC Speaker',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 15
  Mono: Playback 0 [0%] [off]
Simple mixer control 'Aux',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [off] Capture [off]
  Front Right: Playback 0 [0%] [off] Capture [off]
Simple mixer control 'Mono Output Select',0
  Capabilities: enum
  Items: 'Mix' 'Mic'
  Item0: 'Mix'
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch cswitch-joined
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 0 [0%] [on]
  Front Right: Capture 0 [0%] [on]
Simple mixer control 'Mix',0
  Capabilities: cswitch cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Mix Mono',0
  Capabilities: cswitch cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Analog to IEC958 Output',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Channel Mode',0
  Capabilities: enum
  Items: '2ch' '4ch' '6ch'
  Item0: '2ch'
Simple mixer control 'Duplicate Front',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Exchange Center/LFE',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'External Amplifier',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Swap Surround Slot',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
erich@erich-desktop:~$ 

```

In the above, several items are set to 0; for example, Simple mixer control 'Center',0 ... does this mean my sound is muted?  Where do I unmute it?  Yea, stupid question, but I don't see it in the menu's anywhere.  I ran rythmbox music player and it appears the sound is on and NOT muted.

```
erich@erich-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: nForce2 [NVidia nForce2], device 0: Intel ICH [NVidia nForce2]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: nForce2 [NVidia nForce2], device 2: Intel ICH - IEC958 [NVidia nForce2 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
erich@erich-desktop:~$ 
```

Not trying to hijack, loveshocked.  I suggest running amixer and lspci from command line also.

---

### Post by loveshocked on 2007-04-08
I have checked with alsa mixer, everyting is in 100 position

---

### Post by loveshocked on 2007-04-08
**** List of PLAYBACK Hardware Devices ****
card 0: CMI8738 [C-Media PCI CMI8738], device 0: CMI8738 [C-Media PCI DAC/ADC]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: CMI8738 [C-Media PCI CMI8738], device 1: CMI8738 [C-Media PCI 2nd DAC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CMI8738 [C-Media PCI CMI8738], device 2: CMI8738 [C-Media PCI IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
loveshocked@loveshocked-ubuntu:~$ sudo /sbin/modprobe snd- cmi8738
FATAL: Module snd_ not found.

i don't understand why module snd not fount. when i check with alsamixer, what i get are bars (graphical)

thanx

---

### Post by loveshocked on 2007-04-08
# krussell

can't hear anything, even when i log in.

---

### Post by rajeev1204 on 2007-04-08
Hi

By any chance u use gxine or similar media players? 

I had similar problem and found that volume was muted in gxine. Some applications control the master volume so this can happen

Try to remember what u did just before this happened . Open those applications and check sound level

---

### Post by XtremeSki2001 on 2007-04-08
> **rajeev1204 said:**
> Hi

By any chance u use gxine or similar media players? 

I had similar problem and found that volume was muted in gxine. Some applications control the master volume so this can happen

Try to remember what u did just before this happened . Open those applications and check sound level

I've only used Rhtymbox and all is well inside the application (sound isn't muted).  

Besides, I can't help but think there must be volume control that overrides application controls; otherwise, this seems like a very major design flaw.

---

### Post by loveshocked on 2007-04-08
i used xmms. After i installed xirc and samba, it stopped working.. :confused:

---

### Post by Punker on 2007-04-08
> **loveshocked said:**
> **** List of PLAYBACK Hardware Devices ****
card 0: CMI8738 [C-Media PCI CMI8738], device 0: CMI8738 [C-Media PCI DAC/ADC]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: CMI8738 [C-Media PCI CMI8738], device 1: CMI8738 [C-Media PCI 2nd DAC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CMI8738 [C-Media PCI CMI8738], device 2: CMI8738 [C-Media PCI IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
loveshocked@loveshocked-ubuntu:~$ sudo /sbin/modprobe snd- cmi8738

FATAL: Module snd_ not found.

i don't understand why module snd not fount. when i check with alsamixer, what i get are bars (graphical)

thanx

ok here we go I play music so I'm big on sound

```

sudo /sbin/modprobe snd-cmi8738

```

you had a space snd- cmi8738  no space


```

sudo  gedit /etc/modules

```
 when it opens  it should look like this 
```


# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

snd-cmi8738    <<<<<<add this line

lp

```


this all I know how to do with my sound card and this is what fixed my problem if your still havening problems I cant help you because then your haveing other issues
I try to give back because I got a bunch of help here and I learned so much from thies people hope this works:guitar:

---

### Post by XtremeSki2001 on 2007-04-08
> **Punker said:**
> ok here we go I play music so I'm big on sound

```

sudo /sbin/modprobe snd-cmi8738

```

you had a space snd- cmi8738  no space


Space or no space, no luck here.

```
erich@erich-desktop:~$ sudo /sbin/modprobe snd-nForce2
Password:
FATAL: Module snd_nForce2 not found.
erich@erich-desktop:~$ sudo /sbin/modprobe snd-IEC958
FATAL: Module snd_IEC958 not found.
```

---

### Post by loveshocked on 2007-04-08
what I get sudo /sbin/modprobe snd-cmi8738 is

 sudo /sbin/modprobe snd-cmi8738
Password:
FATAL: Module snd_cmi8738 not found.

is it the wrong command or ..?  because, it seems someone else is having the same problem. Can any of you help? :(

---

### Post by Valstorm2323 on 2007-04-10
I have the same problem as of today. I think the updates must have screwed it up.

If you search the forums for NO SOUND then you should be able to find a link that states how to "fix" it.

I haven't done it yet and might not get around to do doing it tonight.

I have of course Ubunty Edgy.

---

### Post by Valstorm2323 on 2007-04-11
have you tried adding these>

options snd-intel8x0 index=0
options snd-ice1712 index=1
options snd-usb-audio index=2

in your alsa-base file, put them at the very bottom.

This seems to fix everyone's problems but I can't seem to get permission to edit the darn thing arhh!

---

### Post by Valstorm2323 on 2007-04-11
Sound is back and here's what my alsa-base looks like now:

# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-intel8x0 index=0
options snd-ice1712 index=1
options snd-usb-audio index=2


I don't know if that's why it's working again but I also put in a soundblaster PCI card and just booted my compe today. Suddenly it's working and the only things I did yesterday was edit alsa-base , turn off computer (was yesterday so I got fed up )
Wake up today, throw in a pci sound card, turn on comp and BOOM I got sound again.

---

### Post by eggdeng on 2007-04-11
Perhaps you are having the same problem as these guys.
[http://ubuntuforums.org/showthread.php?t=406676](http://ubuntuforums.org/showthread.php?t=406676)

---

