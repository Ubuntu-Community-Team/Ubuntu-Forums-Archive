---
title: "Can't change brightness 14.04 (unity)"
date: 2014-10-18
forum: General Help
---

### Post by user1397 on 2014-10-18
I have 14.04.1 with regular unity desktop.  Everything works out of the box, and no additional drivers were needed.  The only thing that doesn't seem to work is brightness adjustment.  I can move it left or right, but the actual brightness stays the same. 

Any ideas?

I have an intel core i5 4th gen with integrated intel HD graphics.

---

### Post by Toz on 2014-10-18
Can we see the results of the following:

1. Your current kernel boot line:
```
cat /proc/cmdline
```

2. Info about your video card(s) and drivers:
```
lspci -k | grep -A2 VGA
```

3. Info about the recognized backlight interfaces:
```
for interface in /sys/class/backlight/*; do echo -e "\n $interface"; cat $interface/{brightness,max_brightness,actual_brightness}; done
```

4. Your currently loaded kernel modules:
```
lsmod
```

5. What, if anything, xorg says about backlight:
```
cat /var/log/Xorg.0.log | grep -i backlight
```

---

### Post by user1397 on 2014-10-18
> **Toz said:**
> Can we see the results of the following:

1. Your current kernel boot line:
```
cat /proc/cmdline
``````
BOOT_IMAGE=/boot/vmlinuz-3.13.0-37-generic.efi.signed root=UUID=ce5ee79f-dce1-4cf9-92f0-bfabc1b8c983 ro quiet splash vt.handoff=7
```

> **Toz said:**
> 2. Info about your video card(s) and drivers:
```
lspci -k | grep -A2 VGA
``````
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 0b)	Subsystem: Acer Incorporated [ALI] Device 0866
	Kernel driver in use: i915

```

> **Toz said:**
> 3. Info about the recognized backlight interfaces:
```
for interface in /sys/class/backlight/*; do echo -e "\n $interface"; cat $interface/{brightness,max_brightness,actual_brightness}; done
``````
 /sys/class/backlight/acpi_video0100
100
100


 /sys/class/backlight/intel_backlight
937
937
937
```

> **Toz said:**
> 4. Your currently loaded kernel modules:
```
lsmod
``````
Module                  Size  Used byusblp                  22891  0 
ctr                    13049  1 
ccm                    17773  1 
pci_stub               12622  1 
vboxpci                23194  0 
vboxnetadp             25670  0 
vboxnetflt             27613  0 
vboxdrv               339502  3 vboxnetadp,vboxnetflt,vboxpci
rfcomm                 69160  8 
bnep                   19624  2 
nls_iso8859_1          12713  1 
snd_hda_codec_hdmi     46368  1 
snd_hda_codec_realtek    65580  1 
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40664  1 uvcvideo
videodev              134688  2 uvcvideo,videobuf2_core
acer_wmi               32522  0 
sparse_keymap          13948  1 acer_wmi
intel_rapl             18773  0 
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       14705  0 
coretemp               13435  0 
kvm_intel             143109  0 
kvm                   451552  1 kvm_intel
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13216  0 
aesni_intel            55624  2 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
btusb                  32412  0 
bluetooth             391136  22 bnep,btusb,rfcomm
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_hda_intel          56451  10 
snd_rawmidi            30144  1 snd_seq_midi
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
arc4                   12608  2 
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
ath9k                 164164  0 
joydev                 17381  0 
ath9k_common           13551  1 ath9k
ath9k_hw              453856  2 ath9k_common,ath9k
serio_raw              13462  0 
ath                    28698  3 ath9k_common,ath9k,ath9k_hw
lpc_ich                21080  0 
mac80211              630653  1 ath9k
cfg80211              484040  3 ath,ath9k,mac80211
rtsx_pci_ms            18151  0 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
memstick               16966  1 rtsx_pci_ms
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
parport_pc             32701  0 
i915                  783805  6 
ppdev                  17671  0 
snd                    69322  31 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
wmi                    19177  1 acer_wmi
video                  19476  2 i915,acer_wmi
drm_kms_helper         55071  1 i915
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
drm                   303102  5 i915,drm_kms_helper
mac_hid                13205  0 
mei_me                 18627  0 
i2c_algo_bit           13413  1 i915
mei                    82276  1 mei_me
soundcore              12680  1 snd
hid_generic            12548  0 
usbhid                 52659  0 
hid                   106148  2 hid_generic,usbhid
rtsx_pci_sdmmc         23274  0 
r8169                  67581  0 
psmouse               106678  0 
ahci                   25819  3 
libahci                32716  1 ahci
mii                    13934  1 r8169
rtsx_pci               46202  2 rtsx_pci_ms,rtsx_pci_sdmmc
```

> **Toz said:**
> 5. What, if anything, xorg says about backlight:
```
cat /var/log/Xorg.0.log | grep -i backlight
``````
[    17.876] (--) intel(0): found backlight control interface acpi_video0 (type 'firmware')
```

---

### Post by Toz on 2014-10-18
Follow [these instructions]("http://ubuntuforums.org/showthread.php?t=2198516&p=12895765&viewfull=1#post12895765") to force X to use the intel_backlight interface for backlight control.

---

### Post by user1397 on 2014-10-18
> **Toz said:**
> Follow [these instructions]("http://ubuntuforums.org/showthread.php?t=2198516&p=12895765&viewfull=1#post12895765") to force X to use the intel_backlight interface for backlight control.That worked perfectly, thank you so much Toz.  Marking as solved.

---

