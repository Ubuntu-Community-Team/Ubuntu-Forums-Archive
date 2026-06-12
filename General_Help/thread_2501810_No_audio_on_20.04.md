---
title: "No audio on 20.04"
date: 2024-10-21
forum: General Help
---

### Post by Kermilli on 2024-10-21
I've been having problems with audio on and off.

I resolved it initially by adding "options snd-hda-intel model=auto" to  /etc/modprobe.d/alsa-base.conf.   

     It worked for some time and then it stopped working while listening to audio.   

sudo dmesg gives me an error [B]
snd_hda_intel 0000:00:1b.0: no codecs found!
[/B]


sudo  pulseaudio -k && sudo alsa force-reload
gives me an error 
[pulseaudio] main.c: Failed to kill daemon: No such process



Devices
```


pol@pol-Precision-M6800:~$ lspci -nnk | grep -A2 Audio
00:03.0 Audio device [0403]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller [8086:0c0c] (rev 06)
    Subsystem: Dell Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller [1028:05cd]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel
--
00:1b.0 Audio device [0403]: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller [8086:8c20] (rev 04)
    Subsystem: Dell 8 Series/C220 Series Chipset High Definition Audio Controller [1028:05cd]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel
--
01:00.1 Audio device [0403]: NVIDIA Corporation GK104 HDMI Audio Controller [10de:0e0a] (rev a1)
    Subsystem: Dell GK104 HDMI Audio Controller [1028:15cd]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel


```


List of devices under aplay:
```


pol@pol-Precision-M6800:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA Intel HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 10: HDMI 4 [HDMI 4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 10: HDMI 4 [HDMI 4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


```


```

pol@pol-Precision-M6800:~$ cat /proc/asound/cards 
 0 [HDMI           ]: HDA-Intel - HDA Intel HDMI
                      HDA Intel HDMI at 0xf7a34000 irq 41
 1 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xf7a30000 irq 38
 2 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xf5080000 irq 17


```

As far as I understand HDA Intel PCH doesnt show under aplay

     I've tried a lot of things but none seem to work or work for a short period.

---

### Post by 1fallen on 2024-10-21
can you include this as well please:
```
sudo dmesg|grep snd_hda

```

Oh crap your still on pluseaudio.....

---

### Post by Kermilli on 2024-10-21
```
sudo dmesg|grep snd_hda
[sudo] password for pol:
[    4.144604] snd_hda_intel 0000:00:03.0: enabling device (0000 -> 0002)
[    4.146092] snd_hda_intel 0000:01:00.1: Disabling MSI
[    4.146106] snd_hda_intel 0000:01:00.1: Handle vga_switcheroo audio client
[    4.148527] snd_hda_intel 0000:00:1b.0: no codecs found!
[    4.474353] snd_hda_intel 0000:00:03.0: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915])
pol@pol-Precision-M6800:~

```


Also systemctl --user status pulseaudio gives
```

systemctl --user status pulseaudio
&#9679; pulseaudio.service - Sound Service
     Loaded: loaded (/usr/lib/systemd/user/pulseaudio.service; enabled; vendor preset: enabled)
     Active: active (running) since Mon 2024-10-21 20:56:47 CEST; 2h 9min ago
TriggeredBy: &#9679; pulseaudio.socket
   Main PID: 1658 (pulseaudio)
     CGroup: /user.slice/user-1000.slice/user@1000.service/pulseaudio.service
             &#9500;&#9472;1658 /usr/bin/pulseaudio --daemonize=no --log-target=journal
             &#9492;&#9472;1669 /usr/libexec/pulse/gsettings-helper

Tet 21 20:56:47 pol-Precision-M6800 systemd[1652]: Starting Sound Service...
Tet 21 20:56:47 pol-Precision-M6800 pulseaudio[1658]: **Failed to find a working profile.**
Tet 21 20:56:47 pol-Precision-M6800 pulseaudio[1658]: **Failed to load module "module-alsa-card" (argument: "device_id="1" name="pci-0000_00_1b.0" card_name="alsa_card.pci-0000_00_1b.0" namereg_fail=false>**
Tet 21 20:56:47 pol-Precision-M6800 systemd[1652]: Started Sound Service.
Tet 21 20:56:47 pol-Precision-M6800 pulseaudio[1658]: **Failed to find a working profile.**
Tet 21 20:56:47 pol-Precision-M6800 pulseaudio[1658]:** Failed to load module "module-alsa-card" (argument: "device_id="1" name="pci-0000_00_1b.0" card_name="alsa_card.pci-0000_00_1b.0" namereg_fail=false>**
lines 1-15/15 (END)

```


I switched  22.04 LTS to 20.04 after having problems with audio there with pipewire. Upgrading to 24.04 didn't help with the audio.

---

### Post by Kermilli on 2024-10-22
The card that drives the internal speakers/PCH wasn't working and it was missing files on proc/asound . I tried copying my respective PCH files from a live cd and when I  booted up on my SSD audio was available again. Hope it helps anyone.

---

