---
title: "GeForce 710M: Not able to change screen brightness"
date: 2014-04-11
forum: General Help
---

### Post by AbhimanyuAryan on 2014-04-11
i am using ubuntu 14.04 final beta & i am not able to change the screen brightness to low or high. Neither from the the system settings nor from the keyboard shortcut keys(fn+required key) :(  please help me to fix it

---

### Post by Toz on 2014-04-11
Lets have a closer look at some of your system settings. Open a terminal window, type in the following commands, and post back the results within **[noparse]```
 
```[/noparse]** tags:

1. What is the make and model of your computer?

2. Your current kernel boot line:
```
cat /proc/cmdline
```
3. Information about your video card(s):
```
lspci -k | grep -iA2 VGA
```
4. Information about your known backlight interfaces:
```
for interface in /sys/class/backlight/*; do echo -e "\n $interface"; cat $interface/{brightness,max_brightness,actual_brightness}; done
```
5. A listing of your loaded kernel modules:
```
lsmod
```
6. Your /var/log/Xorg.0.log file:
```
pastebinit /var/log/Xorg.0.log
```
...and post back the link that is generated.

---

### Post by AbhimanyuAryan on 2014-04-12
sorry pastebinit wasn't installed on my pc so posting it here: 

      ```
abhimanyu@Acer:~$ cat /proc/cmdlineBOOT_IMAGE=/boot/vmlinuz-3.13.0-23-generic root=UUID=bc6f51c5-7821-416c-bdd8-53535a21329f ro quiet splash
```
```
abhimanyu@Acer:~$ lspci -k | grep -iA2 VGA
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
	Subsystem: Acer Incorporated [ALI] Device 0649
	Kernel driver in use: i915
--
01:00.0 VGA compatible controller: NVIDIA Corporation GF117M [GeForce 610M/710M/820M / GT 620M/625M/630M/720M] (rev a1)
	Subsystem: Acer Incorporated [ALI] GeForce 710M
	Kernel driver in use: nvidia
```
```
abhimanyu@Acer:~$ for interface in /sys/class/backlight/*; do echo -e "\n $interface"; cat $interface/{brightness,max_brightness,actual_brightness}; done


 /sys/class/backlight/acpi_video0
10
10
10


 /sys/class/backlight/acpi_video1
10
10
10


 /sys/class/backlight/intel_backlight
976
976
976
```
```
abhimanyu@Acer:~$ lsmod
Module                  Size  Used by
bbswitch               13615  0 
bnep                   18895  2 
rfcomm                 53664  12 
nvidia               9648068  35 
binfmt_misc            13140  1 
arc4                   12536  2 
ath9k                 144602  0 
intel_rapl             18301  0 
joydev                 17101  0 
ath9k_common           13359  1 ath9k
ath9k_hw              438205  2 ath9k_common,ath9k
x86_pkg_temp_thermal    13845  0 
uvcvideo               71309  0 
intel_powerclamp       14239  0 
videobuf2_vmalloc      13048  1 uvcvideo
videobuf2_memops       13170  1 videobuf2_vmalloc
acer_wmi               31735  0 
videobuf2_core         39258  1 uvcvideo
sparse_keymap          13708  1 acer_wmi
ath                    23922  3 ath9k_common,ath9k,ath9k_hw
i915                  705396  2 
mac80211              545990  1 ath9k
videodev              108503  2 uvcvideo,videobuf2_core
ath3k                  13110  0 
coretemp               13195  0 
btusb                  27580  0 
snd_hda_codec_hdmi     45303  1 
kvm_intel             132549  0 
snd_hda_codec_realtek    51029  1 
bluetooth             342263  23 bnep,ath3k,btusb,rfcomm
cfg80211              409394  3 ath,ath9k,mac80211
snd_hda_intel          42730  3 
psmouse                90855  0 
kvm                   388083  1 kvm_intel
snd_hda_codec         164067  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
drm_kms_helper         46907  1 i915
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                85501  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
drm                   243817  5 i915,drm_kms_helper,nvidia
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
i2c_algo_bit           13197  1 i915
snd_rawmidi            25135  1 snd_seq_midi
crc32_pclmul           12967  0 
mei_me                 14099  0 
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
serio_raw              13230  0 
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              28584  2 snd_pcm,snd_seq
mei                    66735  1 mei_me
snd                    60871  17 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
soundcore              12600  1 snd
lpc_ich                16864  0 
wmi                    18673  1 acer_wmi
video                  18856  2 i915,acer_wmi
mac_hid                13037  0 
lp                     13299  0 
parport                40836  1 lp
tg3                   152124  0 
ahci                   25579  2 
sdhci_pci              18535  0 
ptp                    18445  1 tg3
libahci                26754  1 ahci
sdhci                  37779  1 sdhci_pci
pps_core               18799  1 ptp
```

---

### Post by Toz on 2014-04-12
Can you try the **acpi_backlight=vendor** kernel parameter? Follow [these instructions]("Temporarily Add a Kernel Boot Parameter for Testing") to temporarily test it, and when booted with the parameter, post back the results to the commands above again (with acpi_backlight=vendor active).

---

### Post by AbhimanyuAryan on 2014-04-12
this link is not working: [http://temporarily%20add%20a%20kernel%20boot%20parameter%20for%20testing/](http://temporarily%20add%20a%20kernel%20boot%20parameter%20for%20testing/)

---

### Post by AbhimanyuAryan on 2014-04-12
should i follow these instructions on this link:[http://askubuntu.com/questions/128463/how-to-control-brightness](http://askubuntu.com/questions/128463/how-to-control-brightness)
 
seems to work with acer aspire range and i am also using aspire E1-571G :)

---

### Post by Toz on 2014-04-12
> **AbhimanyuAryan said:**
> this link is not working: [http://temporarily%20add%20a%20kernel%20boot%20parameter%20for%20testing/](http://temporarily%20add%20a%20kernel%20boot%20parameter%20for%20testing/)
Sorry. Follow the "Temporarily add a kernel boot parameter for testing" from here: [https://wiki.ubuntu.com/Kernel/KernelBootParameters]("https://wiki.ubuntu.com/Kernel/KernelBootParameters")

---

### Post by Toz on 2014-04-12
> **AbhimanyuAryan said:**
> should i follow these instructions on this link:[http://askubuntu.com/questions/128463/how-to-control-brightness](http://askubuntu.com/questions/128463/how-to-control-brightness)
 
seems to work with acer aspire range and i am also using aspire E1-571G :)
Those are the permanent instructions. i always suggest to try it temporarily first in case it doesn't work, that way all you have to do is reboot to return your system back to the way it was. Once its confirmed to work, we can make the change permanent using those instructions.

---

### Post by AbhimanyuAryan on 2014-04-12
i followed this: [http://askubuntu.com/questions/128463/how-to-control-brightness](http://askubuntu.com/questions/128463/how-to-control-brightness)

 now working perfect :)

---

### Post by Toz on 2014-04-12
Glad to hear the problem is solved. Can you please mark this thread as solved (via the Thread Tools link above) so that others may benefit? Thanks.

---

