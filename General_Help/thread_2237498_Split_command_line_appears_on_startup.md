---
title: "Split command line appears on startup"
date: 2014-08-02
forum: General Help
---

### Post by beardedwondr on 2014-08-02
I'm running xubuntu and almost every time I boot to my desktop a split command line appears. Whenever I type, it adds some illegible characters and as soon as I press enter it boots me to the login screen. Here's a screenshot that shows the issue:

[IMG]http://oi61.tinypic.com/2rcpwme.jpg[/IMG]

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.4 LTS"
NAME="Ubuntu"
VERSION="12.04.4 LTS, Precise Pangolin"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu precise (12.04.4 LTS)"
VERSION_ID="12.04"

---

### Post by kc1di on 2014-08-02
I would start with the video card,  
do you know which driver your using?
if you don't know go to a terminal and type the following commands and list the outputs here. 
```
lspci | grep VGA
``` and
```
lsmod
```

that will give us information to help.

---

### Post by beardedwondr on 2014-08-02
```
lspci | grep VGA
01:00.0 VGA compatible controller: VIA Technologies, Inc. CN896/VN896/P4M900 [Chrome 9 HC] (rev 01)
```
```
lsmod
Module                  Size  Used by
via                    45283  0 
drm                   197641  1 via
vesafb                 13516  1 
joydev                 17393  0 
snd_hda_codec_conexant    52521  1 
snd_hda_intel          32719  3 
snd_hda_codec         109562  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
arc4                   12473  2 
snd_pcm                80916  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
ath5k                 145127  0 
snd_timer              28931  2 snd_pcm,snd_seq
ath                    19387  1 ath5k
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
mac80211              436493  1 ath5k
snd                    62218  15 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              178877  3 ath5k,ath,mac80211
soundcore              14635  1 snd
psmouse                97180  0 
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
i2c_viapro             12969  0 
serio_raw              13027  0 
video                  19115  0 
bnep                   17830  2 
parport_pc             32114  0 
bluetooth             158447  7 bnep
ppdev                  12849  0 
mac_hid                13077  0 
binfmt_misc            17292  1 
shpchp                 32265  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
via_rhine              27413  0 
pata_via               13428  0 
sata_via               13495  2
```

---

### Post by kc1di on 2014-08-02
Basically that's an old Video card and it was at best very problematic in linux.  
The best advice i could offer would be to find a cheap nvidia or intel video card and replace it.

VIA card have never worked well in linux.

---

### Post by beardedwondr on 2014-08-02
That's a shame. It's just an old laptop so I don't think I'll go to the trouble of installing a new graphics card.

---

