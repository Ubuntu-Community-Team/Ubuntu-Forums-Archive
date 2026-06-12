---
title: "Wifi not working upon resume from suspend"
date: 2014-05-13
forum: General Help
---

### Post by josephellengar2 on 2014-05-13
Hi. I am having a problem in that my wireless is not working after I resume from suspend. I'm not sure if the driver is unloaded, but even when I turn off the radio and turn it back on the wireless still doesn't work. In order to get it to work I have to restart the computer.

So far I have tried to go through my loaded drivers and modprobe -r/modprobe them. I also added this script to my /etc/pm/sleep.d but it doesn't work. It is set to execute.

```

#!/bin/bash
case "$1" in
    resume)
        modprobe -r cfg80211;
    modprobe cfg80211;
esac

```

The following is the output from my lsmod:
```

Module                  Size  Used by
snd_hda_codec_hdmi     46207  1 
snd_hda_codec_idt      54645  1 
ctr                    13049  1 
ccm                    17773  1 
hid_multitouch         17407  0 
hid_generic            12548  0 
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40664  1 uvcvideo
usbhid                 52616  0 
videodev              134688  2 uvcvideo,videobuf2_core
hid                   106148  3 hid_multitouch,hid_generic,usbhid
btusb                  32412  0 
joydev                 17381  0 
nouveau              1097199  1 
hp_wmi                 14062  0 
mxm_wmi                13021  1 nouveau
sparse_keymap          13948  1 hp_wmi
arc4                   12608  2 
bnep                   19624  2 
rfcomm                 69160  8 
bluetooth             395423  22 bnep,btusb,rfcomm
iwldvm                232285  0 
mac80211              626489  1 iwldvm
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       14705  0 
coretemp               13435  0 
kvm_intel             143060  0 
snd_hda_intel          52355  5 
kvm                   451511  1 kvm_intel
snd_hda_codec         192906  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
iwlwifi               169932  1 iwldvm
ghash_clmulni_intel    13259  0 
aesni_intel            55624  2 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
binfmt_misc            17468  1 
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
intel_smartconnect     12619  0 
i915                  783485  5 
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
ttm                    85115  1 nouveau
psmouse               102222  0 
wmi                    19177  3 hp_wmi,mxm_wmi,nouveau
drm_kms_helper         52758  2 i915,nouveau
snd                    69238  21 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
hp_accel               26012  0 
serio_raw              13462  0 
drm                   302817  7 ttm,i915,drm_kms_helper,nouveau
lis3lv02d              20156  1 hp_accel
cfg80211              484040  3 iwlwifi,mac80211,iwldvm
video                  19476  2 i915,nouveau
input_polldev          13896  1 lis3lv02d
rtsx_pci_ms            18151  0 
lpc_ich                21080  0 
i2c_algo_bit           13413  2 i915,nouveau
memstick               16966  1 rtsx_pci_ms
soundcore              12680  1 snd
mei_me                 18627  0 
mei                    82274  1 mei_me
mac_hid                13205  0 
parport_pc             32701  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
rtsx_pci_sdmmc         23274  0 
ahci                   25819  4 
r8169                  67581  0 
libahci                32168  1 ahci
rtsx_pci               45956  2 rtsx_pci_ms,rtsx_pci_sdmmc
mii                    13934  1 r8169

```

---

### Post by monkeybrain20122 on 2014-05-13
[http://askubuntu.com/questions/361991/suspend-problems-in-13-10/362148#362148](http://askubuntu.com/questions/361991/suspend-problems-in-13-10/362148#362148)
[https://bugs.launchpad.net/ubuntu/+source/systemd-shim/+bug/1252121](https://bugs.launchpad.net/ubuntu/+source/systemd-shim/+bug/1252121)

---

### Post by josephellengar2 on 2014-05-13
Unfortunately, neither of those worked. I hadn't seen the askubuntu one yet, but I tried it and not luck. Even manually unloading and reloading the iwlwifi driver as below doesn't work.

```
sudo modprobe -r iwlwifi; sudo modprobe iwlwifi;
```

What happens is that when I resume from sleep it says that it detects all of the correct wireless hotspots. Both of mine are in the list, as are my neighbors', but then it gets stuck connecting. It just says "connecting" forever to no avail.

Also, when I run the other suggestion:

```


sudo nmcli nm sleep false


```

I always get this result from the shell:

```

Error in sleep: Already awake

```

So far I haven't been able to resume a single time without having to restart to get back networking.

---

### Post by josephellengar2 on 2014-05-13
Alright, I found a workaround that's worked for at least two suspend/resumes so far. For posterity:

In the directory /etc/pm/sleep.d I put a script (executable of course) that contained the following text:

```

case "$1" in
thaw|resume)
nmcli nm sleep false
pkill -f wpa_supplicant
;;
*)
;;
esac
exit $?

```

---

