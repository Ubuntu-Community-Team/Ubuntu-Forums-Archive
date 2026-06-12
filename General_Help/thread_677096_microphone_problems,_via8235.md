---
title: "microphone problems, via8235"
date: 2008-01-24
forum: General Help
---

### Post by miko3k on 2008-01-24
Hi

gnome-sound-recorder freezes when I push the record button. Mumble freezes either. Haven't tried any other microphone-friendly software but I suspect they would end up the same.

I'm using on-board soundcard on matsonic ms8147c motherboard, via vt8235 southbridge is probably the guy responsible for my sound :-) Sound playback works perfectly though. 

Microphone seems working, when I enable it in volume control I can hear myself.

some possible helpful stuff follows ...

loaded modules:
```

root@miko:/proc/bus/pci# lsmod  | grep via
snd_via82xx            27928  1 
gameport               15240  1 snd_via82xx
snd_ac97_codec         99492  1 snd_via82xx
snd_pcm                77320  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         10504  2 snd_via82xx,snd_pcm
snd_mpu401_uart         8576  1 snd_via82xx
snd                    52356  13 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_viapro              9108  0 
via_ircc               26772  0 
irda                  192316  1 via_ircc
i2c_core               25104  2 nvidia,i2c_viapro
via_agp                10368  1 
agpgart                33584  2 nvidia,via_agp
via_rhine              24200  0 
mii                     5632  1 via_rhine
via82cxxx               9476  0 [permanent]
ide_core              114772  3 ide_disk,ide_cd,via82cxxx

```

lspci output:
```
00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge (rev 80)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 440 AGP 8x] (rev a2)
```

I'm actually pretty lost, have almost no experience with sound recording under linux. Is there some way to diagnose and possibly fix the problem ?

Edit: just spelling fix

---

