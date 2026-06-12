---
title: "touchpad and mouse enabled while suspended"
date: 2014-06-03
forum: General Help
---

### Post by neyson-v on 2014-06-03
hi guys
I have a problem. it's just that when I suspend the computer both touchpad and mouse keep enabled and so just by touching one of them, the computer get resumed which is obviously a wrong behaviour. 
I'm doing a script which disable both touchpad and mouse and then suspend, and once it gets resumed both of them get enabled. this is the script
```

#!/bin/bash
sudo modprobe -r psmouse
xinput --disable 12 
sleep 1
sudo pm-suspend
sudo modprobe psmouse
xinput --enable 12

```
the script success at keeping the touchpad disabled while suspended however, it does not success the same way at keeping mouse disabled because of xinput command behaviour. unfortunately I find no way to disable the mouse by using  modprobe command which behave the way I want. here is the output I get  when I run lsmod
```
 
Module                  Size  Used by
psmouse               102222  0 
ctr                    13049  2 
ccm                    17773  2 
bnep                   19624  2 
rfcomm                 69160  8 
binfmt_misc            17468  1 
snd_hda_codec_hdmi     46207  1 
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40664  1 uvcvideo
videodev              134688  2 uvcvideo,videobuf2_core
intel_rapl             18773  0 
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       14705  0 
coretemp               13435  0 
kvm                   451511  0 
arc4                   12608  2 
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13216  0 
joydev                 17381  0 
aesni_intel            55624  4 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_hda_codec_conexant    57441  1 
serio_raw              13462  0 
ath9k                 164164  0 
ath9k_common           13551  1 ath9k
ath9k_hw              453856  2 ath9k_common,ath9k
ath                    28698  3 ath9k_common,ath9k,ath9k_hw
mac80211              626511  1 ath9k
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_hda_intel          52355  5 
snd_hda_codec         192906  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_rawmidi            30144  1 snd_seq_midi
snd_hwdep              13602  1 snd_hda_codec
rtsx_pci_ms            18151  0 
lpc_ich                21080  0 
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
cfg80211              484040  3 ath,ath9k,mac80211
memstick               16966  1 rtsx_pci_ms
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
snd                    69238  21 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
sony_laptop            54219  0 
ath3k                  13318  0 
btusb                  32412  0 
video                  19476  0 
bluetooth             395423  23 bnep,ath3k,btusb,rfcomm
nvidia              10675249  42 
mei_me                 18627  0 
mei                    82274  1 mei_me
drm                   302817  2 nvidia
soundcore              12680  1 snd
mac_hid                13205  0 
parport_pc             32701  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
hid_generic            12548  0 
usbhid                 52570  0 
hid                   106148  2 hid_generic,usbhid
rtsx_pci_sdmmc         23274  0 
ahci                   25819  3 
r8169                  67581  0 
libahci                32168  1 ahci
rtsx_pci               45956  2 rtsx_pci_ms,rtsx_pci_sdmmc
mii                    13934  1 r8169

```
so is there a way to disable the mouse by using modprobe????
neverthess others ways to fix my problem are welcome :D maybe by editting some file that modify the suspend behaviour or something
thank you in advance guys

---

