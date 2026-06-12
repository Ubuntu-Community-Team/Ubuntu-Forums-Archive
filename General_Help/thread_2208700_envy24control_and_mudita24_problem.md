---
title: "envy24control and mudita24 problem"
date: 2014-03-01
forum: General Help
---

### Post by adde2 on 2014-03-01
hello. im new in ubuntu.

i got ubuntu 64bit 12.04 lts and i cant start envy24control or mudita24
i can see the icon. but nothing happens when i click on it.
how can i fix it.  i need it so i can get my delta 2496 soundcard to work

---

### Post by tgalati4 on 2014-03-01
Open a terminal:

```
mudita24
```

What do you see?

---

### Post by adde2 on 2014-03-02
it only say

No ICE1712 cards found

---

### Post by tgalati4 on 2014-03-02
Try changing the slot that your sound card is plugged in.  Make sure it is reseated properly.  Put your finger on the main chip.  If it is very hot, then your sound card is bad.

---

### Post by adde2 on 2014-03-02
i only got one slot for it. and the card works fine. just tried it on dualboot in windows

---

### Post by tgalati4 on 2014-03-02
Open a terminal and post the output of:

```
lsmod
```

---

### Post by adde2 on 2014-03-02
Code:

Module                  Size  Used by
snd_hda_codec_hdmi     37463  4 
kvm_amd                60277  0 
kvm                   456261  1 kvm_amd
joydev                 17613  0 
hid_generic            12540  0 
hid_logitech_dj        18767  0 
k10temp                13173  0 
snd_hda_codec_realtek    80100  1 
snd_ice1712            75523  0 
snd_ice17xx_ak4xxx     13315  1 snd_ice1712
nvidia              11335129  50 
snd_ak4xxx_adda        18904  2 snd_ice1712,snd_ice17xx_ak4xxx
snd_cs8427             14297  1 snd_ice1712
snd_ac97_codec        134918  1 snd_ice1712
microcode              23075  0 
ac97_bus               12766  1 snd_ac97_codec
snd_hda_intel          44339  5 
snd_i2c                14191  2 snd_ice1712,snd_cs8427
snd_hda_codec         141761  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_mpu401_uart        14169  1 snd_ice1712
snd_hwdep              13668  1 snd_hda_codec
serio_raw              13215  0 
usbhid                 47346  1 hid_logitech_dj
hid                   105826  3 hid_generic,hid_logitech_dj,usbhid
snd_seq_midi           13324  0 
snd_pcm               102477  5 snd_hda_codec_hdmi,snd_ice1712,snd_ac97_codec,snd_hda_intel,snd_hda_codec
snd_rawmidi            30417  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61930  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29989  2 snd_pcm,snd_seq
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    69533  26 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_ice1712,snd_ak4xxx_adda,snd_cs8427,snd_ac97_codec,snd_hda_intel,snd_i2c,snd_hda_codec,snd_mpu401_uart,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_piix4              13459  0 
bnep                   18399  2 
rfcomm                 47922  0 
soundcore              12680  1 snd
snd_page_alloc         18798  2 snd_hda_intel,snd_pcm
mac_hid                13253  0 
bluetooth             247324  10 bnep,rfcomm
parport_pc             28284  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
pata_acpi              13038  0 
pata_atiixp            13271  0 
r8169                  68904  0 
ahci                   25879  2 
libahci                31636  1 ahci

---

### Post by tgalati4 on 2014-03-03
You have the correct modules loaded:

snd_ice1712 75523 0
snd_ice17xx_ak4xxx 13315 1 snd_ice1712
nvidia 11335129 50
snd_ak4xxx_adda 18904 2 snd_ice1712,snd_ice17xx_ak4xxx
snd_cs8427 14297 1 snd_ice1712
snd_ac97_codec 134918 1 snd_ice1712

Turn off your on-board, Intel sound by going into BIOS and turning it off.  You have a conflict between both sound cards and you have to research ways to switch between them.  Verify that the snd_hda_intel modules do not get loaded.

Some reading:

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

---

