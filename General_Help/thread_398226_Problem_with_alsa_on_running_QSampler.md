---
title: "Problem with alsa on running QSampler"
date: 2007-03-31
forum: General Help
---

### Post by bourgi220 on 2007-03-31
Hi everybody,

I just installed QSampler with synaptic. The installation was alright but when i run QSampler and then i want to add a channel, i receive theses errors messages in the programm konsole.

>     ALSA lib control.c:785:(snd_ctl_open_conf) symbol _snd_ctl_hw_open is not defined inside (null)
    AudioOutputDeviceAlsa: Cannot open sound control for card 0 - No such device or address
    ALSA lib control.c:785:(snd_ctl_open_conf) symbol _snd_ctl_hw_open is not defined inside (null)
    AudioOutputDeviceAlsa: Cannot open sound control for card 1 - No such device or address
    AudioOutputDeviceAlsa: Can't find any card

I made shearches with google, i found those links:
J'ai cherché sur google, j'ai notamment trouvé ceci: 
[https://bugs.linuxsampler.org/cgi-bin/show_bug.cgi?id=42](https://bugs.linuxsampler.org/cgi-bin/show_bug.cgi?id=42)
Visibly, the problem doesn't come from the program but from the alsa librairies.

I also found this link: [http://mediatools.cs.ucl.ac.uk/nets/mmedia/changeset/3692](http://mediatools.cs.ucl.ac.uk/nets/mmedia/changeset/3692)
On this link, the author explains some modifications to make in a file to solve the first problem (on which i made my searches). Fist of all, what do you think about theses modifications? And secondly, where is this file? because on my ubuntu edgy, this file is not in the path quoted on the link.

By the way, i don't have any problem with my sound card with other programs. i can read mp3 without any problem.

I hope you'll be able to help me because i'm not the only one.

PS:
I don't know if these informations are interesting but i enter some commands in my console to check my sound card (i found these commands on this site:
[http://philipjm.free.fr/blog/index.php?2006/06/09/42-verifier-la-configuration-alsa](http://philipjm.free.fr/blog/index.php?2006/06/09/42-verifier-la-configuration-alsa)

>     adri@adri-laptop:~$ lspci
    00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
    00:01.0 PCI bridge: VIA Technologies, Inc. VT8235 PCI Bridge
    00:07.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
    00:08.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
    00:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8180L 802.11b MAC (rev 20)
    00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
    00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
    00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
    00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
    00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
    00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
    00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
    00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
    00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
    01:00.0 VGA compatible controller: ATI Technologies Inc M9+ 5C61 [Radeon Mobility 9200 (AGP)] (rev 01)

>     adri@adri-laptop:~$ lsmod | grep snd
    snd_seq_dummy           4996  0
    snd_seq_oss            36480  0
    snd_seq_midi            9984  0
    snd_seq_midi_event      8960  2 snd_seq_oss,snd_seq_midi
    snd_seq                59120  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
    snd_via82xx            30360  4
    gameport               17160  1 snd_via82xx
    snd_mpu401_uart        10240  1 snd_via82xx
    snd_rawmidi            27264  2 snd_seq_midi,snd_mpu401_uart
    snd_seq_device          9868  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
    snd_via82xx_modem      16648  0
    snd_ac97_codec         97696  2 snd_via82xx,snd_via82xx_modem
    snd_ac97_bus            3456  1 snd_ac97_codec
    snd_pcm_oss            47360  0
    snd_mixer_oss          19584  2 snd_pcm_oss
    snd_pcm                84612  5 snd_via82xx,snd_via82xx_modem,snd_ac97_codec,snd_pcm_oss
    snd_timer              25348  2 snd_seq,snd_pcm
    snd                    58372  17 snd_seq_oss,snd_seq,snd_via82xx,snd_mpu401_uart,snd_rawmidi,snd_seq_device,snd_via82xx_modem,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
    soundcore              11232  2 snd
    snd_page_alloc         11400  3 snd_via82xx,snd_via82xx_modem,snd_pcm

>     adri@adri-laptop:~$ cat /proc/asound/cards
    0 [V8235          ]: VIA8233 - VIA 8235
                          VIA 8235 with ALC202 at 0x1400, irq 9
    1 [modem          ]: VIA82XX-MODEM - VIA 82XX modem
                          VIA 82XX modem at 0x1800, irq 9

>     adri@adri-laptop:~$ cat /proc/asound/oss/sndstat
    Sound Driver:3.8.1a-980706 (ALSA v1.0.12rc1 emulation code)
    Kernel: Linux adri-laptop 2.6.17-11-generic #2 SMP Thu Feb 1 19:52:28 UTC 2007 i686
    Config options: 0

    Installed drivers:
    Type 10: ALSA emulation

    Card config:
    VIA 8235 with ALC202 at 0x1400, irq 9
    VIA 82XX modem at 0x1800, irq 9

    Audio devices:
    0: VIA 8235 (DUPLEX)
    1: VIA 82XX modem (DUPLEX)

    Synth devices: NOT ENABLED IN CONFIG

    Midi devices: NOT ENABLED IN CONFIG

    Timers:
    31: system timer

    Mixers:
    0: Realtek ALC202 rev 0
    1: Silicon Laboratory Si3036,8 rev

>     adri@adri-laptop:~$ aplay -l
    **** Liste des PLAYBACK périphériques ****
    carte  0: V8235 [VIA 8235], périphérique 0 : VIA 8235 [VIA 8235]
      Sous-périphériques: 3/4
      Sous-périphérique: #0: subdevice #0
      Sous-périphérique: #1: subdevice #1
      Sous-périphérique: #2: subdevice #2
      Sous-périphérique: #3: subdevice #3
    carte  0: V8235 [VIA 8235], périphérique 1 : VIA 8235 [VIA 8235]
      Sous-périphériques: 1/1
      Sous-périphérique: #0: subdevice #0
    carte  1: modem [VIA 82XX modem], périphérique 0 : VIA 82XX modem [VIA 82XX modem]
      Sous-périphériques: 1/1
      Sous-périphérique: #0: subdevice #0

>     adri@adri-laptop:~$ aplaymidi -l
    Port    Client name                      Port name
    14:0    Midi Through                     Midi Through Port-0

---

### Post by bourgi220 on 2007-04-01
up

---

