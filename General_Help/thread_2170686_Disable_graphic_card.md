---
title: "Disable graphic card"
date: 2013-08-27
forum: General Help
---

### Post by vittorio2 on 2013-08-27
hi there, got Lubuntu 13.04 on Acer v3-571G, going fine :KS

graphic card: nvidia optimus gt630M

to save battery life i installed and configured TLP and Cpu-Freq, but i noticed a huge work of my fan and the notebook is always hot in the gpu zone
i tried to install bumblebee but with no results, from the official site and this one too 
[http://e0d.com/blog/dell-xps-15-l502xrunning-linux-lubuntu-11-04-with-nvidia-optimus-support#comments](http://e0d.com/blog/dell-xps-15-l502xrunning-linux-lubuntu-11-04-with-nvidia-optimus-support#comments)

could you help me? if possible i would prefer to totally disable the nvidiaGPU to use just the intel one :D

---

### Post by lukeiamyourfather on 2013-08-27
There's usually an option in the BIOS or UEFI to select one or other graphics chipset (or both). At least that's the case on my ThinkPad T420 with a Quadro NVS 4200M.

---

### Post by wildmanne39 on 2013-08-27
If the above suggestion does not work post the output from:
```
lspci | grep VGA
```
that will show the driver being used then we can blacklist it.
Thanks

---

### Post by vittorio2 on 2013-08-27
> **Wild Man said:**
> 
```
lspci | grep VGA
```
that will show the driver being used then we can blacklist it.

thank you for your reply! :p

tried it, that's the output

```
 00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
 01:00.0 VGA compatible controller: NVIDIA Corporation GF108M [GeForce GT 630M] (rev a1)
```

PS. (my notebook it's dual booted with win7, i use it for games, so i think it wouldn't be good to disable the nvidiaGPU on boot or similar)

---

### Post by wildmanne39 on 2013-08-27
This should do it:
```
echo "blacklist nvidia" | sudo tee -a /etc/modprobe.d/blacklist.conf

```
Thanks

---

### Post by vittorio2 on 2013-08-27
> **Wild Man said:**
> ```
echo "blacklist nvidia" | sudo tee -a /etc/modprobe.d/blacklist.conf

```

i inserted it in the terminal and obtained ```
blacklist nvidia
```

but if i check with ```
lspci | grep VGA
``` it gives me the same result that appeared before inserting your code ```
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: NVIDIA Corporation GF108M [GeForce GT 630M] (rev a1)
```

does it work? (there are no changes about very hot gpu and heavy fan work)

---

### Post by wildmanne39 on 2013-08-27
Post the output of:
```
lsmod
```
by clicking on new reply and click # then paste the information between the brackets.
Thank you

---

### Post by vittorio2 on 2013-08-28
```
Module                  Size  Used bynvram                  13986  0 
bnep                   17669  2 
rfcomm                 37420  12 
snd_hda_codec_hdmi     36185  1 
snd_hda_codec_realtek    63791  1 
uvcvideo               71279  0 
videobuf2_vmalloc      12920  1 uvcvideo
videobuf2_memops       13042  1 videobuf2_vmalloc
videobuf2_core         39161  1 uvcvideo
videodev               95806  2 uvcvideo,videobuf2_core
ath3k                  12790  0 
btusb                  17986  0 
bluetooth             202109  23 bnep,ath3k,btusb,rfcomm
snd_hda_intel          38307  1 
snd_hda_codec         117580  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
joydev                 17097  0 
arc4                   12543  2 
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                80890  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
nouveau               838609  1 
ath9k                 134875  0 
coretemp               13131  0 
kvm_intel             126842  0 
ath9k_common           13783  1 ath9k
kvm                   376505  1 kvm_intel
ath9k_hw              398477  2 ath9k_common,ath9k
snd_seq_midi           13132  0 
mxm_wmi                12893  1 nouveau
snd_seq_midi_event     14475  1 snd_seq_midi
acer_wmi               27592  0 
ttm                    71289  1 nouveau
snd_rawmidi            25114  1 snd_seq_midi
sparse_keymap          13658  1 acer_wmi
i915                  535544  2 
snd_seq                51280  2 snd_seq_midi_event,snd_seq_midi
ath                    19187  3 ath9k_common,ath9k,ath9k_hw
drm_kms_helper         47545  2 i915,nouveau
wmi                    18590  3 acer_wmi,mxm_wmi,nouveau
mac80211              526519  1 ath9k
video                  18894  3 i915,acer_wmi,nouveau
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
drm                   228489  6 ttm,i915,drm_kms_helper,nouveau
snd_timer              24411  2 snd_pcm,snd_seq
mei                    36197  0 
mac_hid                13037  0 
snd                    56485  12 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
cfg80211              436177  3 ath,ath9k,mac80211
i2c_algo_bit           13197  2 i915,nouveau
soundcore              12600  1 snd
psmouse                81065  0 
serio_raw              13031  0 
lpc_ich                16925  0 
lp                     13299  0 
parport                40753  1 lp
microcode              18286  0 
tg3                   147910  0 
sdhci_pci              18158  0 
ptp                    18189  1 tg3
ahci                   25507  2 
libahci                26108  1 ahci
sdhci                  31824  1 sdhci_pci
pps_core               13736  1 ptp



```

---

### Post by wildmanne39 on 2013-08-28
It is now using the nouveau driver so we will blacklist that as well.
```
echo "blacklist nouveau" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
that should take care of the nividia card being used. As for if that will fix your issue we will have to wait and see but there is a good chance it will help.

---

### Post by vittorio2 on 2013-08-28
ok, i blacklisted the "nouveau" driver thanks to your help, but _there are no changes_.... :sad:

[COLOR=#000000]if i check with[/COLOR][COLOR=#000000]
```
lspci | grep VGA
```
[/COLOR][COLOR=#000000]it gives me the same posted result

any idea?[/COLOR]

---

### Post by wildmanne39 on 2013-08-29
This command ```
lspci | grep VGA
```should give the same results because it lists your graphic card devices in your computer.
```
lsmod
``` shows what drivers are loaded for your cards so if there is no driver loaded then the card is not being used and now that we blacklist both nividia drivers unless you installed another it should not be used now.

---

### Post by vittorio2 on 2013-08-29
i would like to thank you for your help, but i solved the problem in a different way ;)

just reinstalled bumblebee and it's working fine, no more hot notebook or heavy and noisy fan
i think both your commands and the reinstall helped in my case =D>

i'm here if you need other of my posted terminal results in the case they're will be useful to someone.

by now i'm going to post my ```
lsmod
``` hoping it will help someone to resolve this issue  :D

```
bbswitch               13347  0 nvram                  13986  0 
bnep                   17669  2 
rfcomm                 37420  12 
snd_hda_codec_hdmi     36185  1 
snd_hda_codec_realtek    63791  1 
uvcvideo               71279  0 
videobuf2_vmalloc      12920  1 uvcvideo
videobuf2_memops       13042  1 videobuf2_vmalloc
videobuf2_core         39161  1 uvcvideo
videodev               95806  2 uvcvideo,videobuf2_core
ath3k                  12790  0 
btusb                  17986  0 
bluetooth             202109  23 bnep,ath3k,btusb,rfcomm
joydev                 17097  0 
coretemp               13131  0 
snd_hda_intel          38307  1 
kvm_intel             126842  0 
acer_wmi               27592  0 
snd_hda_codec         117580  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
kvm                   376505  1 kvm_intel
snd_hwdep              13272  1 snd_hda_codec
arc4                   12543  2 
ath9k                 134875  0 
snd_pcm                80890  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
sparse_keymap          13658  1 acer_wmi
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25114  1 snd_seq_midi
ath9k_common           13783  1 ath9k
i915                  535544  2 
wmi                    18590  1 acer_wmi
ath9k_hw              398477  2 ath9k_common,ath9k
snd_seq                51280  2 snd_seq_midi_event,snd_seq_midi
ath                    19187  3 ath9k_common,ath9k,ath9k_hw
drm_kms_helper         47545  1 i915
video                  18894  2 i915,acer_wmi
mac80211              526519  1 ath9k
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
drm                   228489  3 i915,drm_kms_helper
snd_timer              24411  2 snd_pcm,snd_seq
mei                    36197  0 
cfg80211              436177  3 ath,ath9k,mac80211
lpc_ich                16925  0 
mac_hid                13037  0 
i2c_algo_bit           13197  1 i915
snd                    56485  12 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
soundcore              12600  1 snd
psmouse                81065  0 
microcode              18286  0 
lp                     13299  0 
parport                40753  1 lp
serio_raw              13031  0 
tg3                   147910  0 
sdhci_pci              18158  0 
ptp                    18189  1 tg3
ahci                   25507  2 
libahci                26108  1 ahci
sdhci                  31824  1 sdhci_pci
pps_core               13736  1 ptp



```


THANK YOU ALL GUYS =D>=D>

---

### Post by wildmanne39 on 2013-08-29
Lsmod shows that you are only using the intel card your nvidia has been deactivated.

---

