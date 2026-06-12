---
title: "Asus x102ba screen brightness"
date: 2014-03-29
forum: General Help
---

### Post by bryncoles on 2014-03-29
Hi all.  

I Got a new 10" Asus x102ba.  As seems typical with Ausu though, adjusting the screen brightness seems not to work!  Ooops!  Anyone have any ideas?  I have tried adding various "acpi=vendor" switches to Grub with no effect, and have tried acpitools, though it tells me that there are no Asus modules on this laptop!

Suggestions / advice?  At the least, what software should control the brightness, and how I can file a bug report?

Cheers all!

---

### Post by bryncoles on 2014-03-29
Further information:

Running (found in another thread):
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/actual_brightness; cat $i/max_brightness; done
```

 tells me:

> cat: /sys/class/backlight/*/brightness: No such file or directory
cat: /sys/class/backlight/*/actual_brightness: No such file or directory
cat: /sys/class/backlight/*/max_brightness: No such file or directory

if that helps...

---

### Post by Toz on 2014-03-29
Lets have a closer look at some of your system settings. Open a terminal window, type in the following commands, and post back the results within **[noparse]```
 
```[/noparse]** tags:

1. Your current kernel boot line:
```
cat /proc/cmdline
```
2. Information about your video card(s):
```
lspci -k | grep -iA2 VGA
```
3. Information about your known backlight interfaces:
```
for interface in /sys/class/backlight/*; do echo -e "\n $interface"; cat $interface/{brightness,max_brightness,actual_brightness}; done
```
4. A listing of your loaded kernel modules:
```
lsmod
```
5. Your /var/log/Xorg.0.log file:
```
pastebinit /var/log/Xorg.0.log
```
...and post back the link that is generated.

---

### Post by bryncoles on 2014-03-29
Hi!  Thanks for joining in to help!

Results for the first command are:
```
cat /proc/cmdline
```
```
BOOT_IMAGE=/boot/vmlinuz-3.11.0-18-generic root=UUID=82b24a0a-dc7d-4c36-8f59-bc562ce84833 ro quiet splash nomodeset vt.handoff=7
```

and for the second:
```
lspci -k | grep -iA2 VGA
```
```
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Kabini [Radeon HD 8180]
	Subsystem: ASUSTeK Computer Inc. Device 141d
00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Device 9840
antikythera@antikythera-X102BA:~$ 
```

The third:

```
for interface in /sys/class/backlight/*; do echo -e "\n $interface"; cat $interface/{brightness,max_brightness,actual_brightness}; done
```

```
 /sys/class/backlight/*
cat: /sys/class/backlight/*/brightness: No such file or directory
cat: /sys/class/backlight/*/max_brightness: No such file or directory
cat: /sys/class/backlight/*/actual_brightness: No such file or directory
```

the fourth:

```
lsmod
```
```
Module                  Size  Used by
vesafb                 13828  1 
amd_freq_sensitivity    12589  0 
kvm_amd                59987  0 
kvm                   431754  1 kvm_amd
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13259  0 
aesni_intel            55624  0 
parport_pc             32701  0 
aes_x86_64             17131  1 aesni_intel
ppdev                  17671  0 
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
joydev                 17377  0 
asus_nb_wmi            16990  0 
asus_wmi               24191  1 asus_nb_wmi
sparse_keymap          13948  1 asus_wmi
rfcomm                 69130  0 
bnep                   19704  2 
bluetooth             372041  10 bnep,rfcomm
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
snd_hda_codec_realtek    56475  1 
videobuf2_core         40499  1 uvcvideo
videodev              133509  2 uvcvideo,videobuf2_core
hid_multitouch         17407  0 
snd_hda_codec_hdmi     41154  1 
arc4                   12608  2 
microcode              23656  0 
snd_hda_intel          52267  5 
ath9k                 155779  0 
ath9k_common           13859  1 ath9k
snd_hda_codec         188738  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
ath9k_hw              444732  2 ath9k_common,ath9k
ath                    23827  3 ath9k_common,ath9k,ath9k_hw
psmouse                97655  0 
snd_pcm               102033  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
edac_core              62342  0 
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
serio_raw              13413  0 
edac_mce_amd           22617  0 
mac80211              597268  1 ath9k
fam15h_power           13119  0 
k10temp                13126  0 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
i2c_piix4              22106  0 
cfg80211              480503  3 ath,ath9k,mac80211
snd_rawmidi            30095  1 snd_seq_midi
wmi                    19070  1 asus_wmi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
radeon               1408158  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29433  2 snd_pcm,snd_seq
ttm                    84169  1 radeon
drm_kms_helper         52710  1 radeon
mac_hid                13205  0 
drm                   297056  3 ttm,drm_kms_helper,radeon
snd                    69141  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
video                  19318  1 asus_wmi
soundcore              12680  1 snd
i2c_algo_bit           13413  1 radeon
lp                     17759  0 
parport                42299  3 lp,ppdev,parport_pc
usbhid                 53014  0 
hid                   101762  2 hid_multitouch,usbhid
sdhci_pci              18981  0 
sdhci                  42898  1 sdhci_pci
r8169                  67581  0 
ahci                   25819  2 
mii                    13934  1 r8169
libahci                32009  1 ahci
```

and lastly:

[pastebinit /var/log/Xorg.0.log](http://paste.ubuntu.com/7174173/)

Let's see what happens next!  ^_^

---

### Post by Toz on 2014-03-29
You're not using any of the ATI drivers, your system is defaulting to VESA drivers (which don't have backlight support). This is probably because of your use of the nomodeset kernel parameter.

What version of Xubuntu are you using? 
Do you have any ATI drivers specified in "Additional Drivers"?
Have you tried installing them?

---

### Post by bryncoles on 2014-03-29
Hi Toz  

I'm running Xubutu 13:10, fully updated.  

If I try and run Xubuntu without the nomodeset, it will not boot.  The 'additional drivers' menu gives me three options:

Using Xorg X server AMD/ATI display driver wrapper from xserver-xorg-video-ati (open source)  (recommended)  ===>  This is the one I'm currently using. 
Using video driver for the AMD graphics accelerators from fglrx (proprietary)
Using video driver for the AMD graphics accelerators from fglrx-updates (proprietary)

I have tried all three, with no benefits from the second two.  Still no ability to toggle brightness!

Any thoughts?

---

### Post by Toz on 2014-03-29
> Using Xorg X server AMD/ATI display driver wrapper from xserver-xorg-video-ati (open source) (recommended) ===> This is the one I'm currently using. 
Can you post back again the results of the commands from post #3?

And if possible, install the "Using video driver for the AMD graphics accelerators from fglrx (proprietary)" option and after a reboot, post back those results again for this driver.

---

### Post by bryncoles on 2014-03-29
Hi Toz.  

Thanks for joining in.  Here's the command again:

First:
```
cat /proc/cmdline
```
```
BOOT_IMAGE=/boot/vmlinuz-3.11.0-18-generic root=UUID=82b24a0a-dc7d-4c36-8f59-bc562ce84833 ro quiet splash nomodeset vt.handoff=7[\code]

Second:
[code] lspci -k | grep -iA2 VGA
```
```
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Kabini [Radeon HD 8180]
	Subsystem: ASUSTeK Computer Inc. Device 141d
00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Device 9840
```

Third:
```
for interface in /sys/class/backlight/*; do echo -e "\n $interface"; cat $interface/{brightness,max_brightness,actual_brightness}; done
```
```
 /sys/class/backlight/*
cat: /sys/class/backlight/*/brightness: No such file or directory
cat: /sys/class/backlight/*/max_brightness: No such file or directory
cat: /sys/class/backlight/*/actual_brightness: No such file or directory
```

Fourth:
```
 lsmod
```
```
Module                  Size  Used by
vesafb                 13828  1 
amd_freq_sensitivity    12589  0 
kvm_amd                59987  0 
kvm                   431754  1 kvm_amd
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13259  0 
aesni_intel            55624  0 
parport_pc             32701  0 
aes_x86_64             17131  1 aesni_intel
ppdev                  17671  0 
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
joydev                 17377  0 
asus_nb_wmi            16990  0 
asus_wmi               24191  1 asus_nb_wmi
sparse_keymap          13948  1 asus_wmi
rfcomm                 69130  0 
bnep                   19704  2 
bluetooth             372041  10 bnep,rfcomm
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
snd_hda_codec_realtek    56475  1 
videobuf2_core         40499  1 uvcvideo
videodev              133509  2 uvcvideo,videobuf2_core
hid_multitouch         17407  0 
snd_hda_codec_hdmi     41154  1 
arc4                   12608  2 
microcode              23656  0 
snd_hda_intel          52267  10 
ath9k                 155779  0 
ath9k_common           13859  1 ath9k
snd_hda_codec         188738  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
ath9k_hw              444732  2 ath9k_common,ath9k
ath                    23827  3 ath9k_common,ath9k,ath9k_hw
psmouse                97655  0 
snd_pcm               102033  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
edac_core              62342  0 
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
serio_raw              13413  0 
edac_mce_amd           22617  0 
mac80211              597268  1 ath9k
fam15h_power           13119  0 
k10temp                13126  0 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
i2c_piix4              22106  0 
cfg80211              480503  3 ath,ath9k,mac80211
snd_rawmidi            30095  1 snd_seq_midi
wmi                    19070  1 asus_wmi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
radeon               1408158  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29433  2 snd_pcm,snd_seq
ttm                    84169  1 radeon
drm_kms_helper         52710  1 radeon
mac_hid                13205  0 
drm                   297056  3 ttm,drm_kms_helper,radeon
snd                    69141  31 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
video                  19318  1 asus_wmi
soundcore              12680  1 snd
i2c_algo_bit           13413  1 radeon
lp                     17759  0 
parport                42299  3 lp,ppdev,parport_pc
usbhid                 53014  0 
hid                   101762  2 hid_multitouch,usbhid
sdhci_pci              18981  0 
sdhci                  42898  1 sdhci_pci
r8169                  67581  0 
ahci                   25819  2 
mii                    13934  1 r8169
libahci                32009  1 ahci
```

Fifth and final:
[http://paste.ubuntu.com/7176072/](http://paste.ubuntu.com/7176072/)

Now, if you'll excuse me a minute, I'll see about installing the "Using video driver for the AMD graphics accelerators from fglrx (proprietary)" option and post them all again!

---

### Post by bryncoles on 2014-03-29
Ok, I'm back.  The commands, with the proprietary drivers running are as follow:

First:
```
cat /proc/cmdline
```
```
BOOT_IMAGE=/boot/vmlinuz-3.11.0-18-generic root=UUID=82b24a0a-dc7d-4c36-8f59-bc562ce84833 ro quiet splash nomodeset vt.handoff=7
```

Second:
```
lspci -k | grep -iA2 VGA
```
```
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Kabini [Radeon HD 8180]
	Subsystem: ASUSTeK Computer Inc. Device 141d
	Kernel driver in use: fglrx_pci
```

Third:
```
for interface in /sys/class/backlight/*; do echo -e "\n $interface"; cat $interface/{brightness,max_brightness,actual_brightness}; done
```
```
 /sys/class/backlight/*
cat: /sys/class/backlight/*/brightness: No such file or directory
cat: /sys/class/backlight/*/max_brightness: No such file or directory
cat: /sys/class/backlight/*/actual_brightness: No such file or directory
```

Fourth:
```
lsmod
```
```
Module                  Size  Used by
vesafb                 13828  1 
bnep                   19704  2 
amd_freq_sensitivity    12589  0 
kvm_amd                59987  0 
rfcomm                 69130  0 
kvm                   431754  1 kvm_amd
bluetooth             372041  10 bnep,rfcomm
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13259  0 
aesni_intel            55624  0 
aes_x86_64             17131  1 aesni_intel
parport_pc             32701  0 
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
ppdev                  17671  0 
asus_nb_wmi            16990  0 
snd_hda_codec_realtek    56475  1 
glue_helper            13990  1 aesni_intel
joydev                 17377  0 
asus_wmi               24191  1 asus_nb_wmi
ablk_helper            13597  1 aesni_intel
sparse_keymap          13948  1 asus_wmi
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_hda_codec_hdmi     41154  1 
uvcvideo               80885  0 
snd_hda_intel          52267  10 
arc4                   12608  2 
videobuf2_vmalloc      13216  1 uvcvideo
ath9k                 155779  0 
snd_hda_codec         188738  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
videobuf2_memops       13362  1 videobuf2_vmalloc
snd_hwdep              13602  1 snd_hda_codec
videobuf2_core         40499  1 uvcvideo
ath9k_common           13859  1 ath9k
ath9k_hw              444732  2 ath9k_common,ath9k
videodev              133509  2 uvcvideo,videobuf2_core
fglrx                6732964  85 
snd_pcm               102033  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
hid_multitouch         17407  0 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
ath                    23827  3 ath9k_common,ath9k,ath9k_hw
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
microcode              23656  0 
mac80211              597268  1 ath9k
snd_rawmidi            30095  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29433  2 snd_pcm,snd_seq
cfg80211              480503  3 ath,ath9k,mac80211
psmouse                97655  0 
edac_core              62342  0 
snd                    69141  31 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
fam15h_power           13119  0 
k10temp                13126  0 
soundcore              12680  1 snd
edac_mce_amd           22617  0 
serio_raw              13413  0 
i2c_piix4              22106  0 
wmi                    19070  1 asus_wmi
amd_iommu_v2           19054  1 fglrx
video                  19318  1 asus_wmi
mac_hid                13205  0 
lp                     17759  0 
parport                42299  3 lp,ppdev,parport_pc
usbhid                 53014  0 
hid                   101762  2 hid_multitouch,usbhid
sdhci_pci              18981  0 
sdhci                  42898  1 sdhci_pci
ahci                   25819  2 
r8169                  67581  0 
libahci                32009  1 ahci
mii                    13934  1 r8169
```

And finally:
[pastebinit /var/log/Xorg.0.log](http://paste.ubuntu.com/7176139/)

Thanks for the help!

---

### Post by Toz on 2014-03-29
Still no backlight interface. 
Okay, lets work with the proprietary drivers first. 

Following the "Temporarily Add a Kernel Boot Parameter for Testing" instructions from the [KernelBootParameters]("https://wiki.ubuntu.com/Kernel/KernelBootParameters") wiki, can you add the **acpi_backlight=vendor** kernel boot parameter? Once logged in, post back the results to those commands again. Lets see if we can get a backlight interface.

---

### Post by bryncoles on 2014-03-30
Hi.  Sorry I have been late joining in today.

Here's the commands again, with the proprietary drivers installed.  

First:
```
cat /proc/cmdline
```
```
BOOT_IMAGE=/boot/vmlinuz-3.11.0-18-generic root=UUID=82b24a0a-dc7d-4c36-8f59-bc562ce84833 ro quiet splash acopi_backlight=vendor nomodeset vt.handoff=7
```

Second:
```
lspci -k | grep -iA2 VGA
```
```
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Kabini [Radeon HD 8180]
	Subsystem: ASUSTeK Computer Inc. Device 141d
	Kernel driver in use: fglrx_pci
```

Third:
```
for interface in /sys/class/backlight/*; do echo -e "\n $interface"; cat $interface/{brightness,max_brightness,actual_brightness}; done
```
```
 /sys/class/backlight/*
cat: /sys/class/backlight/*/brightness: No such file or directory
cat: /sys/class/backlight/*/max_brightness: No such file or directory
cat: /sys/class/backlight/*/actual_brightness: No such file or directory
```

Fourth:
```
lsmod
```
```
Module                  Size  Used by
vesafb                 13828  1 
amd_freq_sensitivity    12589  0 
kvm_amd                59987  0 
kvm                   431754  1 kvm_amd
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13259  0 
aesni_intel            55624  0 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
joydev                 17377  0 
parport_pc             32701  0 
ppdev                  17671  0 
asus_nb_wmi            16990  0 
asus_wmi               24191  1 asus_nb_wmi
sparse_keymap          13948  1 asus_wmi
rfcomm                 69130  0 
bnep                   19704  2 
bluetooth             372041  10 bnep,rfcomm
arc4                   12608  2 
ath9k                 155779  0 
hid_multitouch         17407  0 
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
ath9k_common           13859  1 ath9k
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40499  1 uvcvideo
videodev              133509  2 uvcvideo,videobuf2_core
ath9k_hw              444732  2 ath9k_common,ath9k
microcode              23656  0 
ath                    23827  3 ath9k_common,ath9k,ath9k_hw
snd_hda_codec_realtek    56475  1 
mac80211              597268  1 ath9k
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_hda_codec_hdmi     41154  1 
snd_rawmidi            30095  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_hda_intel          52267  10 
cfg80211              480503  3 ath,ath9k,mac80211
psmouse                97655  0 
snd_hda_codec         188738  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
k10temp                13126  0 
edac_core              62342  0 
edac_mce_amd           22617  0 
serio_raw              13413  0 
fam15h_power           13119  0 
snd_hwdep              13602  1 snd_hda_codec
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_pcm               102033  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_timer              29433  2 snd_pcm,snd_seq
i2c_piix4              22106  0 
fglrx                6732964  166 
wmi                    19070  1 asus_wmi
snd                    69141  31 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
video                  19318  1 asus_wmi
mac_hid                13205  0 
soundcore              12680  1 snd
amd_iommu_v2           19054  1 fglrx
lp                     17759  0 
parport                42299  3 lp,ppdev,parport_pc
usbhid                 53014  0 
hid                   101762  2 hid_multitouch,usbhid
sdhci_pci              18981  0 
sdhci                  42898  1 sdhci_pci
ahci                   25819  2 
r8169                  67581  0 
libahci                32009  1 ahci
mii                    13934  1 r8169
```

Finally:
[pastebinit /var/log/Xorg.0.log](http://paste.ubuntu.com/7180320/)

Now:  There is something else interesting as well.  Looking in the settings manager, using this proprietary driver has added an option called 'AMD catalyst Control Centre'.  This has some fancy options, including brightness settings under the heading 'colour'.  Here, brightness runs from -100 to 100 (default at 0).  This doesn't seem to be 'brightness' as we would traditionally understand the term.  i.e., it seems to toggle the gamma, rather than the brightness per se.

---

### Post by Toz on 2014-03-30
Oops, you misspelled the parameter:
> BOOT_IMAGE=/boot/vmlinuz-3.11.0-18-generic root=UUID=82b24a0a-dc7d-4c36-8f59-bc562ce84833 ro quiet splash **[COLOR="#FF0000"]acopi_backlight=vendor[/COLOR]** nomodeset vt.handoff=7
Can you try again? The parameter is **acpi_backlight=vendor**.


And after you re-try that one, try this one as well: **acpi_osi='!Windows 2012'** (replacing acpi_backlight=vendor).


In both cases, post back all results.

---

### Post by bryncoles on 2014-03-31
Ooops!  Pardon my stubby fingers!  Let's try again:

First:
```
cat /proc/cmdline
```
```
BOOT_IMAGE=/boot/vmlinuz-3.11.0-18-generic root=UUID=82b24a0a-dc7d-4c36-8f59-bc562ce84833 ro quiet splash acpi_backlight=vendor nomodeset vt.handoff=7
```

Second:
```
lspci -k | grep -iA2 VGA
```
```
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Kabini [Radeon HD 8180]
	Subsystem: ASUSTeK Computer Inc. Device 141d
	Kernel driver in use: fglrx_pci
```

Third:
```
for interface in /sys/class/backlight/*; do echo -e "\n $interface"; cat $interface/{brightness,max_brightness,actual_brightness}; done
```

```
/sys/class/backlight/asus-nb-wmi
100
100
100
```

Fourth:
```
lsmod
```
```
Module                  Size  Used by
parport_pc             32701  0 
ppdev                  17671  0 
bnep                   19704  2 
rfcomm                 69130  0 
bluetooth             372041  10 bnep,rfcomm
vesafb                 13828  1 
amd_freq_sensitivity    12589  0 
kvm_amd                59987  0 
kvm                   431754  1 kvm_amd
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13259  0 
aesni_intel            55624  0 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
joydev                 17377  0 
asus_nb_wmi            16990  0 
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
asus_wmi               24191  1 asus_nb_wmi
fglrx                6732964  73 
uvcvideo               80885  0 
sparse_keymap          13948  1 asus_wmi
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
arc4                   12608  2 
videobuf2_core         40499  1 uvcvideo
snd_hda_codec_realtek    56475  1 
ath9k                 155779  0 
snd_hda_codec_hdmi     41154  1 
videodev              133509  2 uvcvideo,videobuf2_core
ath9k_common           13859  1 ath9k
ath9k_hw              444732  2 ath9k_common,ath9k
snd_hda_intel          52267  5 
hid_multitouch         17407  0 
ath                    23827  3 ath9k_common,ath9k,ath9k_hw
snd_hda_codec         188738  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
mac80211              597268  1 ath9k
microcode              23656  0 
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
cfg80211              480503  3 ath,ath9k,mac80211
snd_rawmidi            30095  1 snd_seq_midi
snd_hwdep              13602  1 snd_hda_codec
edac_core              62342  0 
psmouse                97655  0 
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_pcm               102033  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
fam15h_power           13119  0 
wmi                    19070  1 asus_wmi
edac_mce_amd           22617  0 
serio_raw              13413  0 
k10temp                13126  0 
i2c_piix4              22106  0 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29433  2 snd_pcm,snd_seq
snd                    69141  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
soundcore              12680  1 snd
amd_iommu_v2           19054  1 fglrx
video                  19318  1 asus_wmi
mac_hid                13205  0 
lp                     17759  0 
parport                42299  3 lp,ppdev,parport_pc
usb_storage            62062  0 
usbhid                 53014  0 
hid                   101762  2 hid_multitouch,usbhid
sdhci_pci              18981  0 
ahci                   25819  2 
r8169                  67581  0 
sdhci                  42898  1 sdhci_pci
libahci                32009  1 ahci
mii                    13934  1 r8169
```

And finally, 
[pastebinit /var/log/Xorg.0.log](http://paste.ubuntu.com/7184104/)

And gimme a mo and I'l try the other version.  Looks like something changed here though!  Feels like progress! ^_^

---

### Post by bryncoles on 2014-03-31
Ok, and with the acpi_osi='!Windows 2012' the commands result in the following:

First:
```
cat /proc/cmdline
```
```
BOOT_IMAGE=/boot/vmlinuz-3.11.0-18-generic root=UUID=82b24a0a-dc7d-4c36-8f59-bc562ce84833 ro quiet splash "acpi_osi=!Windows 2012" nomodeset vt.handoff=7
```

Second:
```
lspci -k | grep -iA2 VGA
```
```
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Kabini [Radeon HD 8180]
	Subsystem: ASUSTeK Computer Inc. Device 141d
	Kernel driver in use: fglrx_pci
```

Third:
```
for interface in /sys/class/backlight/*; do echo -e "\n $interface"; cat $interface/{brightness,max_brightness,actual_brightness}; done
```
```
 /sys/class/backlight/*
cat: /sys/class/backlight/*/brightness: No such file or directory
cat: /sys/class/backlight/*/max_brightness: No such file or directory
cat: /sys/class/backlight/*/actual_brightness: No such file or directory
```

Fourth:
```
lsmod
```
```
Module                  Size  Used by
vesafb                 13828  1 
amd_freq_sensitivity    12589  0 
kvm_amd                59987  0 
kvm                   431754  1 kvm_amd
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13259  0 
aesni_intel            55624  0 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
joydev                 17377  0 
asus_nb_wmi            16990  0 
parport_pc             32701  0 
asus_wmi               24191  1 asus_nb_wmi
ppdev                  17671  0 
sparse_keymap          13948  1 asus_wmi
snd_hda_codec_realtek    56475  1 
uvcvideo               80885  0 
snd_hda_codec_hdmi     41154  1 
videobuf2_vmalloc      13216  1 uvcvideo
rfcomm                 69130  0 
videobuf2_memops       13362  1 videobuf2_vmalloc
snd_hda_intel          52267  5 
bnep                   19704  2 
bluetooth             372041  10 bnep,rfcomm
videobuf2_core         40499  1 uvcvideo
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
arc4                   12608  2 
snd_hda_codec         188738  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
videodev              133509  2 uvcvideo,videobuf2_core
snd_rawmidi            30095  1 snd_seq_midi
hid_multitouch         17407  0 
ath9k                 155779  0 
snd_hwdep              13602  1 snd_hda_codec
ath9k_common           13859  1 ath9k
microcode              23656  0 
ath9k_hw              444732  2 ath9k_common,ath9k
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
ath                    23827  3 ath9k_common,ath9k,ath9k_hw
mac80211              597268  1 ath9k
snd_pcm               102033  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
psmouse                97655  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
serio_raw              13413  0 
edac_core              62342  0 
k10temp                13126  0 
snd_timer              29433  2 snd_pcm,snd_seq
edac_mce_amd           22617  0 
fam15h_power           13119  0 
cfg80211              480503  3 ath,ath9k,mac80211
i2c_piix4              22106  0 
fglrx                6732964  62 
snd                    69141  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
soundcore              12680  1 snd
amd_iommu_v2           19054  1 fglrx
wmi                    19070  1 asus_wmi
video                  19318  1 asus_wmi
mac_hid                13205  0 
lp                     17759  0 
parport                42299  3 lp,ppdev,parport_pc
usbhid                 53014  0 
hid                   101762  2 hid_multitouch,usbhid
sdhci_pci              18981  0 
sdhci                  42898  1 sdhci_pci
ahci                   25819  2 
r8169                  67581  0 
libahci                32009  1 ahci
mii                    13934  1 r8169
```

Finally:
[pastebinit /var/log/Xorg.0.log](http://paste.ubuntu.com/7184135/)

Thanks!

---

### Post by Toz on 2014-03-31
> **bryncoles said:**
> Ooops!  Pardon my stubby fingers!  Let's try again:

First:
```
cat /proc/cmdline
```
```
BOOT_IMAGE=/boot/vmlinuz-3.11.0-18-generic root=UUID=82b24a0a-dc7d-4c36-8f59-bc562ce84833 ro quiet splash acpi_backlight=vendor nomodeset vt.handoff=7
```

Second:
```
lspci -k | grep -iA2 VGA
```
```
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Kabini [Radeon HD 8180]
	Subsystem: ASUSTeK Computer Inc. Device 141d
	Kernel driver in use: fglrx_pci
```

Third:
```
for interface in /sys/class/backlight/*; do echo -e "\n $interface"; cat $interface/{brightness,max_brightness,actual_brightness}; done
```

```
/sys/class/backlight/asus-nb-wmi
100
100
100
```

Fourth:
```
lsmod
```
```
Module                  Size  Used by
parport_pc             32701  0 
ppdev                  17671  0 
bnep                   19704  2 
rfcomm                 69130  0 
bluetooth             372041  10 bnep,rfcomm
vesafb                 13828  1 
amd_freq_sensitivity    12589  0 
kvm_amd                59987  0 
kvm                   431754  1 kvm_amd
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13259  0 
aesni_intel            55624  0 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
joydev                 17377  0 
asus_nb_wmi            16990  0 
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
asus_wmi               24191  1 asus_nb_wmi
fglrx                6732964  73 
uvcvideo               80885  0 
sparse_keymap          13948  1 asus_wmi
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
arc4                   12608  2 
videobuf2_core         40499  1 uvcvideo
snd_hda_codec_realtek    56475  1 
ath9k                 155779  0 
snd_hda_codec_hdmi     41154  1 
videodev              133509  2 uvcvideo,videobuf2_core
ath9k_common           13859  1 ath9k
ath9k_hw              444732  2 ath9k_common,ath9k
snd_hda_intel          52267  5 
hid_multitouch         17407  0 
ath                    23827  3 ath9k_common,ath9k,ath9k_hw
snd_hda_codec         188738  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
mac80211              597268  1 ath9k
microcode              23656  0 
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
cfg80211              480503  3 ath,ath9k,mac80211
snd_rawmidi            30095  1 snd_seq_midi
snd_hwdep              13602  1 snd_hda_codec
edac_core              62342  0 
psmouse                97655  0 
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_pcm               102033  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
fam15h_power           13119  0 
wmi                    19070  1 asus_wmi
edac_mce_amd           22617  0 
serio_raw              13413  0 
k10temp                13126  0 
i2c_piix4              22106  0 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29433  2 snd_pcm,snd_seq
snd                    69141  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
soundcore              12680  1 snd
amd_iommu_v2           19054  1 fglrx
video                  19318  1 asus_wmi
mac_hid                13205  0 
lp                     17759  0 
parport                42299  3 lp,ppdev,parport_pc
usb_storage            62062  0 
usbhid                 53014  0 
hid                   101762  2 hid_multitouch,usbhid
sdhci_pci              18981  0 
ahci                   25819  2 
r8169                  67581  0 
sdhci                  42898  1 sdhci_pci
libahci                32009  1 ahci
mii                    13934  1 r8169
```

And finally, 
[pastebinit /var/log/Xorg.0.log](http://paste.ubuntu.com/7184104/)

And gimme a mo and I'l try the other version.  Looks like something changed here though!  Feels like progress! ^_^

Good. acpi_backlight=vendor exposes a backlight interface for you (/sys/class/backlight/asus-nb-wmi). Can you try these commands to see if you can manually affect brightness:
```
echo 50 | sudo tee /sys/class/backlight/asus-nb-wmi/brightness
echo 75 | sudo tee /sys/class/backlight/asus-nb-wmi/brightness
echo 100 | sudo tee /sys/class/backlight/asus-nb-wmi/brightness
```
If it works, check your function keys to see if they can adjust the brightness as well.

---

### Post by bryncoles on 2014-03-31
Ok, soi I tried all three commands  

```
echo 50 | sudo tee /sys/class/backlight/asus-nb-wmi/brightness
echo 75 | sudo tee /sys/class/backlight/asus-nb-wmi/brightness
echo 100 | sudo tee /sys/class/backlight/asus-nb-wmi/brightness
```

But to no effect.  I cannot at this time affect brightness.  Boo!  

So, what to try next?

---

### Post by Toz on 2014-03-31
That's unfortunate. Found [this entry]("http://www.linlap.com/asus_x102ba") about your laptop, where the author states that brightness appears to be broken, yet fixed in newer versions of the catalyst driver (which unfortunately breaks suspend). Perhaps its best to create a [bug report]("https://help.ubuntu.com/community/ReportingBugs") for this.

---

### Post by bryncoles on 2014-03-31
Hi Toz.  

Aw, boo!  So, we hit the wall.  Still, the good news is we found out where the wall was, and how hard to run at it ^_^.  

So, but report is created.  Thanks for your efforts here -- hopefully the bug will be resolved soon!

---

