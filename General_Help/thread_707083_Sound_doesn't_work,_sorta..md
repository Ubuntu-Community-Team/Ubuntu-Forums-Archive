---
title: "Sound doesn't work, sorta."
date: 2008-02-25
forum: General Help
---

### Post by Stunned_flounder on 2008-02-25
I switched over to Gutsy from XP on a computer I bought parts for and put together myself.  Now that I switched, I don't get any sound for Skype.  Doing a test-call comes up with an error from Skype saying "Call Failed: Problem with Audio Capture"  or "Call Failed: Problem with Audio Playback."

I have a feeling that the problem lies with ALSA, but when I type "alsamixer" into the terminal, I get this:

```
alsamixer: function snd_ctl_open failed for default: No such device

```

I tried updating to the newest version of ALSA, but one of the instructions (from [https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")) confuses me.  When I'm putting in these codes:

```
sudo mkdir -p /usr/src/alsa
cd /usr/src/alsa
sudo cp ~/downloads/alsa* .
sudo tar xjf alsa-driver*.bz2
sudo tar xjf alsa-lib*.tar.bz2
sudo tar xjf alsa-utils*.tar.bz2

```

I'm not sure what the asterisk means, there's no indicator in the guide.  I don't exactly know the way to use these codes, Is there anyone who could enlighten me a bit on how I could get this to work, or if possible, a better/more direct way to get my sound working for Skype?

Any help would be appreciated, thanks.

---

### Post by JimBuntu on 2008-02-25
I switched from window xp to ubuntu and my sound went out all together. It was an old computer and could have been a hardware problem, but I was guessing it was somehow the drivers not being set up correctly. Tried to fix but couldnt.

---

### Post by danwood76 on 2008-02-25
What soundcard do you have on your machine?

Could you post the output of this:
```

lspci -v | grep Audio

```

---

### Post by Stunned_flounder on 2008-02-25
I didn't get an output when I type that in.  I know I have a Creative SB Audigy card in my computer, and I disabled my onboard sound card in one of my earlier attempts to get sound in Skype.

---

### Post by danwood76 on 2008-02-25
Im not sure about how to setup sound for that card, I dont think creative support linux but you could try their site for a driver anyway.

You will have more luck with your onboard sound card instead of the audigy.

Have a search around the forums, im sure someone has tried to use an audigy before with ubutntu

---

### Post by kpkeerthi on 2008-02-25
I have Audigy 2 ZS and it worked out-of-the box. The only creative card that I'm aware having problems with Linux is the X-Fi series (which will soon be supported).

Try this [Comprehensive Sound Problem Solutions Guide]("http://ubuntuforums.org/showthread.php?t=205449") for some troubleshooting tips.

---

### Post by Stunned_flounder on 2008-02-25
Man, total bummer...I'd a little sad to not be able to use my creative card.  But, I managed to get sound for everything else but Skype.  It's the weirdest thing, does anyone else have this same problem?

The output I get for typing in lspci -v is:

```
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 81)
        Subsystem: Intel Corporation Unknown device 2580
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 81) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: ccf00000-ceffffff
        Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
        Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        I/O behind bridge: 0000d000-0000dfff
        Capabilities: <access denied>

00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 0000c000-0000cfff
        Memory behind bridge: cce00000-ccefffff
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01) (prog-if 00 [UHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 8179
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at 6000 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01) (prog-if 00 [UHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 8179
        Flags: bus master, medium devsel, latency 0, IRQ 21
        I/O ports at 6400 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01) (prog-if 00 [UHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 8179
        Flags: bus master, medium devsel, latency 0, IRQ 22
        I/O ports at 6800 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01) (prog-if 00 [UHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 8179
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at 7000 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01) (prog-if 20 [EHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 8179
        Flags: bus master, medium devsel, latency 0, IRQ 20
        Memory at cccff800 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        I/O behind bridge: 00009000-0000bfff
        Memory behind bridge: ccd00000-ccdfffff
        Prefetchable memory behind bridge: 00000000cff00000-00000000cfffffff
        Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
        Subsystem: ASUSTeK Computer Inc. Unknown device 8179
        Flags: bus master, medium devsel, latency 0
        Capabilities: <access denied>

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
        Subsystem: ASUSTeK Computer Inc. Unknown device 8179
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at ffa0 [size=16]

00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: ASUSTeK Computer Inc. Unknown device 2601
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
        I/O ports at 8800 [size=8]
        I/O ports at 8400 [size=4]
        I/O ports at 8000 [size=8]
        I/O ports at 7800 [size=4]
        I/O ports at 7400 [size=16]
        Memory at cccffc00 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
        Subsystem: ASUSTeK Computer Inc. Unknown device 8179
        Flags: medium devsel, IRQ 6
        I/O ports at 0400 [size=32]

01:01.0 Multimedia audio controller: Creative Labs SB Audigy LS
        Subsystem: Creative Labs Unknown device 100a
        Flags: bus master, medium devsel, latency 64, IRQ 23
        I/O ports at 9800 [size=32]
        Capabilities: <access denied>

01:02.0 Communication controller: 3Com Corp, Modem Division USR 56k Internal WinModem
        Subsystem: 3Com Corp, Modem Division Unknown device 00c2
        Flags: medium devsel, IRQ 5
        Memory at cffffc00 (32-bit, prefetchable) [size=64]
        Memory at cffe0000 (32-bit, prefetchable) [size=64K]
        Memory at cfff0000 (32-bit, prefetchable) [size=32K]
        I/O ports at a000 [size=64]
        Capabilities: <access denied>

01:03.0 Mass storage controller: Integrated Technology Express, Inc. ITE 8211F Single Channel UDMA 133 (rev 11)
        Subsystem: ASUSTeK Computer Inc. P5GD1-VW Mainboard
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 20
        I/O ports at b800 [size=8]
        I/O ports at b400 [size=4]
        I/O ports at b000 [size=8]
        I/O ports at a800 [size=4]
        I/O ports at a400 [size=16]
        Expansion ROM at cff00000 [disabled] [size=128K]
        Capabilities: <access denied>

02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 19)
        Subsystem: ASUSTeK Computer Inc. Marvell 88E8053 Gigabit Ethernet controller PCIe (Asus)
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at ccefc000 (64-bit, non-prefetchable) [size=16K]
        I/O ports at c800 [size=256]
        Expansion ROM at ccec0000 [disabled] [size=128K]
        Capabilities: <access denied>

04:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GT] (rev a1) (prog-if 00 [VGA])
        Subsystem: eVga.com. Corp. Unknown device c615
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at ce000000 (32-bit, non-prefetchable) [size=16M]
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        Memory at cd000000 (64-bit, non-prefetchable) [size=16M]
        I/O ports at e800 [size=128]
        [virtual] Expansion ROM at ccfe0000 [disabled] [size=128K]
        Capabilities: <access denied>

```

My creative card (Creative Labs SB Audigy LS) is listed as the multimedia audio controller, but not as the sound card (? I forgot what the onboard was set under before I disabled it)

Is there a way no way I can make my computer recognize the creative card as the go-to card for all sound?

Sorry, that's in no way technical.  I'm a huge n00b.

---

### Post by danwood76 on 2008-02-26
Yes there is, you can set the default sound card in:
/etc/modprobe.d/alsa-base

First you need to find out which sound module is being loaded to give you sound.
Please post the output of:
```

sudo lsmod | grep snd

```
and
```

cat /etc/modprobe.d/alsa-base

```

That will help us configure the alsa config file.

---

### Post by superprash2003 on 2008-02-26
try this [http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html](http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html)

---

### Post by Stunned_flounder on 2008-02-26
Output for sudo lsmod | grep snd:

```
snd_ca0106             36384  4 
snd_ac97_codec        101668  1 snd_ca0106
snd_pcm_oss            43136  0 
snd_pcm                80388  5 snd_ca0106,snd_ac97_codec,snd_pcm_oss
snd_mixer_oss          17792  1 snd_pcm_oss
snd_seq_dummy           4868  0 
snd_seq_oss            34944  0 
snd_seq_midi            9600  0 
snd_rawmidi            25984  2 snd_ca0106,snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                54000  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24452  2 snd_pcm,snd_seq
snd_seq_device          9484  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56068  17 snd_ca0106,snd_ac97_codec,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
ac97_bus                3200  1 snd_ac97_codec
snd_page_alloc         11400  2 snd_ca0106,snd_pcm

```

and for cat /etc/modprobe.d/alsa-base:

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
options snd-0106 index=0
options snd-hda_intel index=1
```

I haven't re-enabled my onboard sound card yet, do you want the readout after I do that?

---

### Post by Nepherte on 2008-02-26
I've had a similar problem but with a snd-hda-intel card.What I did to fix it, is
```
cp -v /lib/modules/2.6.22-*/kernel/sound/pci/hda/snd-hda-intel.ko /lib/modules/2.6.22-*/ubuntu/media/snd-hda-intel/snd-hda-intel.ko
cp -v /usr/src/alsa/alsa-driver*/modules/* /lib/modules/2.6.22-*/kernel/sound/
depmod -a
```
and restart. You might have to do something similar **but with the correct audio module**.

---

### Post by danwood76 on 2008-02-26
Right you need to modify the last 2 lines in your /etc/modprobe.d/alsa-base

so in terminal
```

sudo gedit /etc/modprobe.d/alsa-base

```
and change the last 2 lines:
```

options snd-0106 index=0
options snd-hda_intel index=1

```
to:
```

options snd-ca0106 index=0
options snd-hda_intel index=1

```

That should make it load the correct module as card 0 (your first card)
obviously for some reason the module name was wrong in that file.

Save it and reboot and post your results.

-- edit --

I just had a look on the ALSA soundscard matrix and noticed something listed by the ca0106 driver
'Digital/Analog input does not work yet. Needs more development work.'

This page may be out dated so it may still work for you but otherwise you should look into getting your onboard hda-intel card working instead.

---

### Post by Stunned_flounder on 2008-02-26
> **Nepherte said:**
> I've had a similar problem but with a snd-hda-intel card.What I did to fix it, is
```
cp -v /lib/modules/2.6.22-*/kernel/sound/pci/hda/snd-hda-intel.ko /lib/modules/2.6.22-*/ubuntu/media/snd-hda-intel/snd-hda-intel.ko
cp -v /usr/src/alsa/alsa-driver*/modules/* /lib/modules/2.6.22-*/kernel/sound/
depmod -a
```
and restart. You might have to do something similar **but with the correct audio module**.

What do the asterisks mean?  Should I just type it in as is (with the exception of changing "snd-hda-intel" to "snd-ca0106" or is there something else I should do?

---

### Post by danwood76 on 2008-02-26
Those commands wont help.
That will only work if you had installed the snd-hda-inte in the wrong place.
The stars are a wildcard they mean any character, any number of characters.

I would try editing the modprobe config file for the alsa drivers, though as I read on the alsa site you may not be able to get analogue in on your sound card.

If you dont then you may be able to setup your internal as a secondary sound card used for input only (or throw the audigy in the bin and just use the internal sound)

---

### Post by Stunned_flounder on 2008-02-26
I rebooted and enabled Intel HD Audio Controller, but still no sound from Skype.


Output of sudo lsmod | grep snd:

```
snd_ca0106             36384  4 
snd_ac97_codec        101668  1 snd_ca0106
snd_hda_intel         296352  4 
snd_hwdep              10372  1 snd_hda_intel
snd_pcm_oss            43136  0 
snd_pcm                80388  8 snd_ca0106,snd_ac97_codec,snd_hda_intel,snd_pcm_oss
snd_mixer_oss          17792  1 snd_pcm_oss
snd_seq_dummy           4868  0 
snd_seq_oss            34944  0 
snd_seq_midi            9600  0 
snd_rawmidi            25984  2 snd_ca0106,snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                54000  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24452  2 snd_pcm,snd_seq
snd_seq_device          9484  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56068  25 snd_ca0106,snd_ac97_codec,snd_hda_intel,snd_hwdep,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ac97_bus                3200  1 snd_ac97_codec
snd_page_alloc         11400  3 snd_ca0106,snd_hda_intel,snd_pcm
soundcore               8800  1 snd

```

If I were to have my onboard sound card start taking the workload, what are the steps I want to take in order to get sound on skype working?

---

### Post by danwood76 on 2008-02-27
Follow my directions in post 12 but change the last two lines to:

```

options snd-hda_intel index=0
options snd-ca0106 index=1

```

This will change the priority so snd_hda_intel is card 0 (the first card). Save the file and reboot.
If this doesnt work could you post the output of:
```

lspci -v | grep Audio
lspci -v | grep audio
cat /proc/asound/cards

```

---

