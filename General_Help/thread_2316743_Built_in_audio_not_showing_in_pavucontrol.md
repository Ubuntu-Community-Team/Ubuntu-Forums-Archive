---
title: "Built in audio not showing in pavucontrol"
date: 2016-03-10
forum: General Help
---

### Post by marsdenf on 2016-03-10
Installed xubuntu 14.04 on a new desktop computer, and "built in audio"  does not show up in pulse audio volume control in the configuration tab.  However, "audio codec" for my digital (usb) speakers does show up.  I am able to get sound with these speakers, but I want to get built in audio back in case I should want to use analog speakers in the future.  Here is the output of inxi -A :
                         
                                           marsdenf@marsdenf-Z170X-Gaming-3:~$ inxi -A
Audio:     Card-1: NVIDIA Device 0fbc driver: snd_hda_intel Sound: ALSA ver: k3.19.0-51-generic
           Card-2: Intel Sunrise Point-H HD Audio driver: snd_hda_intel 
           Card-3: Texas Instruments Audio Codec driver: USB Audio 
           Card-5: Logitech Webcam C270 driver: USB Audio 
marsdenf@marsdenf-Z170X-Gaming-3:~$ 


Here is the ouput of      lspci -v | grep -B1 -A12  -i  audio  :

                                          marsdenf@marsdenf-Z170X-Gaming-3:~$ lspci -v | grep -B1 -A12 -i audio

00:1f.3 Audio device: Intel Corporation Sunrise Point-H HD Audio (rev 31)
    Subsystem: Gigabyte Technology Co., Ltd Device a0b2
    Flags: fast devsel, IRQ 16
    Memory at df320000 (64-bit, non-prefetchable) [size=16K]
    Memory at df300000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel

00:1f.4 SMBus: Intel Corporation Sunrise Point-H SMBus (rev 31)
    Subsystem: Gigabyte Technology Co., Ltd Device 5001
    Flags: medium devsel, IRQ 10
    Memory at df32a000 (64-bit, non-prefetchable) [disabled] [size=256]
    I/O ports at f000 [size=32]
--

01:00.1 Audio device: NVIDIA Corporation Device 0fbc (rev a1)
    Subsystem: eVga.com. Corp. Device 3751
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at df080000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel

03:00.0 PCI bridge: Intel Corporation Device 1578 (rev 03) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=03, secondary=04, subordinate=08, sec-latency=0
    I/O behind bridge: 00002000-00003fff
    Memory behind bridge: df200000-df2fffff
    Prefetchable memory behind bridge: 0000000089800000-0000000089bfffff
marsdenf@marsdenf-Z170X-Gaming-3:~$ 


I tried purging and reinstalling alsa and pulseaudio, followed by force reload of alsa, but that didn't work.  Also tried plugging in analog speakers, but that didn't work either.
Any suggestions?

---

### Post by QDR06VV9 on 2016-03-10
Have tried this yet
```
rm -rf ~/.pulse
rm -rf ~/.config/pulse
```
Don't forget to kill pulseaudio and restart it after doing this, or just reboot.
EDIT: Your card is this one  as "Sound Blaster Recon3Di" is this correct?
If so see this for some bad news [http://askubuntu.com/questions/725265/sound-only-out-of-internal-speakers-never-headphones-alienware-laptop-ubuntu](http://askubuntu.com/questions/725265/sound-only-out-of-internal-speakers-never-headphones-alienware-laptop-ubuntu)

---

### Post by marsdenf on 2016-03-10
Runrickus, I just tried the commands you suggested and it didn't work

---

### Post by QDR06VV9 on 2016-03-10
Did you have a look at the link in my post..

---

### Post by marsdenf on 2016-03-10
Runrickus, I don't know if that is the sound card I have.   Is there any command or program I can run to find out?
I should mention that I recently installed Lubuntu 14.04 on a separate hard drive on the same computer, and built in audio shows up in pulse audio control
in that drive.

---

### Post by QDR06VV9 on 2016-03-10
Well that is odd? do not why one would see it and the not Xunbuntu?
lets look at this slightly more detailed readout of...

```
    lspci -nnk |grep udio
```

---

### Post by marsdenf on 2016-03-10
Here is the output of that command:

                marsdenf@marsdenf-Z170X-Gaming-3:~$ lspci -nnk |grep udio
00:1f.3 Audio device [0403]: Intel Corporation Sunrise Point-H HD Audio [8086:a170] (rev 31)
01:00.1 Audio device [0403]: NVIDIA Corporation Device [10de:0fbc] (rev a1)
marsdenf@marsdenf-Z170X-Gaming-3:~$

---

### Post by QDR06VV9 on 2016-03-10
Ok seems you might need to upgrade ALSA
See This: [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)

EDIT: Also maybe the LTS Enablement Stacks might need the upgrade
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

I have seen more post's saying the upgrade to 15.10 solved sound and network issues

---

