---
title: "SiS NO Sound"
date: 2008-01-30
forum: General Help
---

### Post by Pandab34R on 2008-01-30
I have a foxconn mobo with an sis soundcard(which is being recognized by ubuntu). I have done alsamixer and made sure nothing was muted or turned down. Nothing was. Now I dont know what to do. I read the SoundTroubleshooting and it doesn't seem to make sense to me what I need to do in that situation. Somone please help. Im pretty new with linux.

---

### Post by Pandab34R on 2008-01-31
I discovered that my audio chipset is- SiS 661FX + 964 

I dont see that model in the Vendor Matrix at the AlsaProject wiki... I really need this to work so I can give this machine to my friend in full-working order. I would like to have linux make a great impression on him.

---

### Post by happyhamster on 2008-01-31
Not sure if I can help, but could you show the output of the following commands:

lspci
aplay -l
cat /proc/asound/cards
cat /proc/asound/modules
cat /etc/modprobe.d/alsa-base

---

### Post by Pandab34R on 2008-01-31
> **happyhamster said:**
> Not sure if I can help, but could you show the output of the following commands:

lspci
aplay -l
cat /proc/asound/cards
cat /proc/asound/modules
cat /etc/modprobe.d/alsa-base

lspci

```

miles@WPJAYS52:~$ lspci
0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX Host (rev 11)
0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)
0000:00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller0000:00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
0000:00:05.0 IDE interface: Silicon Integrated Systems [SiS] RAID bus controller 180 SATA/PATA  [SiS] (rev 01)
0000:00:08.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
0000:00:09.0 Communication controller: Conexant HSF 56k HSFi Modem (rev 01)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc R350 AH [Radeon 9800]
0000:01:00.1 Display controller: ATI Technologies Inc Radeon R350 [Radeon 9800] (Secondary)

```

aplay -l
```

0 [SI7012         ]: ICH - SiS SI7012
                     SiS SI7012 with ALC655 at 0xe000, irq 225

```

```

**** List of PLAYBACK Hardware Devices ****
card 0: SI7012 [SiS SI7012], device 0: Intel ICH [SiS SI7012]
  Subdevices: 1/1

```

cat /proc/asound/cards

```

0 [SI7012         ]: ICH - SiS SI7012
                     SiS SI7012 with ALC655 at 0xe000, irq 225


```

cat /proc/asound/modules

```

0 snd_intel8x0

```

cat /etc/modprobe.d/alsa-base
```

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

```

---

### Post by happyhamster on 2008-01-31
Ok, so Ubuntu sees the card and loads the module. This is a tough one...

What you could try first:

- check all physical outputs: it's possible that there's sound coming from an unexpected source (like the microphone jack or such).
- try different audio devices/mixers in the Preferences-->Sound menu
- /proc/asound/cards says: SiS SI7012 with ALC655 at 0xe000, irq 225. If you have easy access to the pc's bios, you can check what the bios thinks the irq for the onboard sound should be. Don't change anything in the bios though (!). (Do you have a pc or a laptop BTW?)

- lspci says: 0000:00:09.0 Communication controller: Conexant HSF 56k HSFi Modem (rev 01)
Just a wild shot: sometimes modem drivers are seen as audio devices (although nothing shows in /proc/asound/modules). If you don't use the modem, then blacklisting its module could help. Well, perhaps :)

Good luck, and let us know.

---

### Post by happyhamster on 2008-01-31
Oh, and what ubuntu version are you using exactly? (uname -r). AMD64 or regular?

---

### Post by Pandab34R on 2008-01-31
I have ubuntu 6.06 LTS 2.6.15-26-386 its regular, non amd64

---

### Post by Pandab34R on 2008-01-31
I think I did something wrong... All of my fonts are appearing as blocks. Illegible, just squares where the letters should be... Lol this sucks worse than having no sound. Holy crap. Any Ideas what I did?

---

### Post by Pandab34R on 2008-02-02
> **Pandab34R said:**
> I think I did something wrong... All of my fonts are appearing as blocks. Illegible, just squares where the letters should be... Lol this sucks worse than having no sound. Holy crap. Any Ideas what I did?

Okay, forget about that, I fixed the problem. Now I am back to where we started. I have no sound, but I am positive ubuntu recognizes my chipset. I have done alsamixer and nothing is muted and no levels are set low. Even alsamixer recognizes my card as: SiS SI7012  and chipset as: Realtek ALC655 rev 1. Im stumped. I think this means that its obviously recognized. But does it mean that the drivers are installed for it?? I really need to get this system up and running for my friend - hes getting impatient :P

---

### Post by Pandab34R on 2008-02-03
bump

---

### Post by happyhamster on 2008-02-03
Just found this:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/58339](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/58339)

Apparently, "External Amplifier" needs to be muted. Then open the menu Preferences-->Sound and try different devices/mixers (well, that's in Gutsy Gibbon, I don't know the menu entries in dapper).

---

### Post by Pandab34R on 2008-02-03
I muted the external amp. didnt do anything, I looked for other sound mixers in the sound prefrences but the SIS S17012 is the only one that is avaliable, even after downloading the alsa drivers from synaptic.

---

### Post by Pandab34R on 2008-02-05
Bump.?

---

### Post by busmas on 2008-02-06
i don't know whether this will help. i had a problem with my foxconn 661fx7mj with no sound until i put a couple of jumpers across pins 5,6 and 9,10 on the front audio port. this stops the front audio port taking priority over the rear audio port where i had my speakers plugged in.

---

