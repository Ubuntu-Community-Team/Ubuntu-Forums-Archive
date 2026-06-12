---
title: "Only Getting 2.1 Sound From Audigy SE"
date: 2007-12-28
forum: General Help
---

### Post by jlacroix on 2007-12-28
Hello everyone.

I had an Audigy card in this same computer, in this same install just about two weeks ago. It was working perfectly.

I gave the Audigy card to my wife, because hers went dead. I have the option of using onboard audio, she doesn't.

My onboard card is a Realtek, and once I started using it, I realized that it sucks.

To replace the original Audigy card I gave my wife, I bought an Audigy SE for my PC. I disabled the onboard Realtek in the bios and installed the card. The card works, but only with 2.1. I do not get any sound from my center or rear speakers whatsoever. I made sure all the sliders are turned all the way up.

Here is some info from lsmod if it will help:
```
Module                  Size  Used by
ipv6                  317192  10 
af_packet              28172  2 
binfmt_misc            14860  1 
dock                   12264  0 
button                 10400  0 
video                  21140  0 
sbs                    21520  0 
container               6400  0 
ac                      7304  0 
battery                12424  0 
sbp2                   27144  0 
ieee1394              109528  1 sbp2
lp                     15048  0 
snd_ca0106             40480  3 
snd_ac97_codec        122200  1 snd_ca0106
snd_pcm_oss            50048  0 
snd_mixer_oss          20096  1 snd_pcm_oss
snd_pcm                94344  4 snd_ca0106,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           5380  0 
snd_seq_oss            36864  0 
snd_seq_midi           11008  0 
snd_rawmidi            29824  2 snd_ca0106,snd_seq_midi
snd_seq_midi_event      9984  2 snd_seq_oss,snd_seq_midi
snd_seq                62496  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
xpad                   11400  0 
snd_timer              27272  3 snd_pcm,snd_seq
snd_seq_device         10260  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
nvidia               7013492  24 
snd                    69288  14 snd_ca0106,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              10272  1 snd
ac97_bus                4096  1 snd_ac97_codec
k8temp                  7680  0 
serio_raw               9092  0 
i2c_viapro             11544  0 
snd_page_alloc         12560  2 snd_ca0106,snd_pcm
parport_pc             41896  1 
parport                44172  2 lp,parport_pc
psmouse                45596  0 
pcspkr                  4608  0 
i2c_core               30208  2 nvidia,i2c_viapro
shpchp                 38300  0 
pci_hotplug            36612  1 shpchp
via_agp                13056  0 
joydev                 13440  0 
evdev                  13056  4 
ext3                  146576  1 
jbd                    69360  1 ext3
mbcache                11272  1 ext3
sg                     41384  0 
usbhid                 32576  0 
hid                    33408  1 usbhid
sd_mod                 32512  5 
ide_cd                 35488  0 
cdrom                  41768  1 ide_cd
sata_via               14596  3 
ehci_hcd               40076  0 
uhci_hcd               29600  0 
floppy                 69608  0 
ata_generic             9988  0 
libata                138928  2 sata_via,ata_generic
scsi_mod              172856  4 sbp2,sg,sd_mod,libata
via_rhine              28936  0 
mii                     7424  1 via_rhine
usbcore               161584  5 xpad,usbhid,ehci_hcd,uhci_hcd
via82cxxx              11268  0 [permanent]
ide_core              141200  2 ide_cd,via82cxxx
thermal                16528  0 
processor              36232  1 thermal
fan                     6920  0 
fuse                   52528  3 
apparmor               47008  0 
commoncap               9472  1 apparmor

```

Edit: I forgot to mention that my card supports 5.1 and 7.1 surround, and my speakers are 5.1. My speakers have a green, yellow, and black cord; and my sound card has an input for each one marked 1, 2, and 3.

---

### Post by jlacroix on 2007-12-29
I thought I figured it out by saving a custom asoundrc file that I found on Google, however it makes the sound full of static in KDE, and sometimes in KDE Amarok cannot access the sound server. I guess I'm almost there, but as of right now it's working but with static. I'm not having many problems in Gnome, though.

Can one of you guru's please help me out? I know it's late at night but I'll sleep easier if I fix this. :)


Here is the asoundrc file I created that gets all speakers working but with static sound: (The file wasn't there already, so I'm wondering if creating it was a good idea, as perhaps it's been obsoleted and the configuration moved somewhere else or possibly the values in this file aren't compatible with Gutsy since the file was created for an earlier Ubuntu version).

[code]################################################## #######
#This is the standard setting (see: "!default")
#This profile, the default loaded, upmixes stereo sound to 5.1.

pcm.!default {
type plug
slave.pcm "surround51"
slave.channels 6
route_policy duplicate
}
################################################## ######
#This is the normal spdif output profile (optical, toslink).

pcm.!spdif {
type plug
slave.pcm "hw:0,1"
}

################################################## #####
#This is what one could call the "factory default setting", in other words, it only plays the actual channels. so if you fx want to watch a 5.1 movie, on the analog output, this is the option you want.


pcm.analog {
type plug
slave analog_slave;
}

pcm_slave.analog_slave {
pcm surround51;
format S32_LE;
}[/'code]

Also, with that script, it seems as if only one application can give me sound at one time.

---

