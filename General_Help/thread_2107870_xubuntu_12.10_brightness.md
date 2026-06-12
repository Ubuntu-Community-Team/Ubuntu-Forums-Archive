---
title: "xubuntu 12.10 brightness"
date: 2013-01-23
forum: General Help
---

### Post by saiaN on 2013-01-23
hi everybody, i have problems with the brightness in xubuntu 12.10, first i have a notebook toshiba satellite sp4216sl with amd graphics and processor amd dual core e300 with 2gb ram.
The problem is that i can't change the brightness in the desktop while i work, see videos,play, or other thing, i can change the brightness modifying etc/rc.local but this is 
uncomfortable because i have to reboot the notebook every time that want change the brightness.
I install the brightness plugin xfce4 but for some reason dont work.

Any help is appreciated

---

### Post by Toz on 2013-01-23
Hello and welcome to the forums.

1. Have you installed the proprietary AMD drivers (Software Centre, Edit->Sources, Additional Drivers tab)?

2. Have you tried any of the following kernel boot parameters:
- acpi_backlight=vendor
- acpi_osi=
- acpi_osi=Linux acpi_backlight=vendor
...See: [https://wiki.ubuntu.com/Kernel/KernelBootParameters]("https://wiki.ubuntu.com/Kernel/KernelBootParameters") for information on how to test these parameters.

3. What is the command that you are using in /etc/rc.local that changes the brightness?

---

### Post by saiaN on 2013-01-23
> **Toz said:**
> Hello and welcome to the forums.

1. Have you installed the proprietary AMD drivers (Software Centre, Edit->Sources, Additional Drivers tab)?

2. Have you tried any of the following kernel boot parameters:
- acpi_backlight=vendor
- acpi_osi=
- acpi_osi=Linux acpi_backlight=vendor
...See: [https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) for information on how to test these parameters.

3. What is the command that you are using in /etc/rc.local that changes the brightness?

1. YES

2. you can explain this please

3. sudo nano/etc/rc.local
echo 4 > /sys/class/backlight/acpi_video0/brightness

thx

---

### Post by saiaN on 2013-01-23
i try with this 

ls /sys/class/backlight

and show

acpi_video0  toshiba

after

sudo bash -c "echo 5 > /sys/class/backlight/acpi_video0/brightness"

but con toshiba dont work

and this work but i want use the brightness plugin for more confortabylity

---

### Post by Toz on 2013-01-23
> 2. you can explain this please

Kernel boot parameters are used to enable, change, and/or disable certain default behaviours of the underlying kernel. In this particular case, these kernel boot parameters will affect how the acpi subsystem is recognized and dealt with by the operating system:

- **acpi_backlight=vendor** - means to perfer the vendor-specific backlight driver over the built-in acpi one. This may force it to use the toshiba backlight interface instead of the acpi_video0 one.

- **acpi_osi=** - means to not announce what your operating system is to your BIOS. In some cases, like Toshiba laptops, there appear to be separate acpi tables for windows and non-windows systems. By not announcing that you are Linux, it may force the load of the Windows tables.

- **acpi_osi=Linux acpi_backlight=vendor** - this one will force the load of the Linux acpi tables (in the event there is confusion) as well as prefer the use of the vendor backlight driver.

You can test the parameters temporarily by following the "Temporarily Add a Kernel Boot Parameter for Testing" instructions at [this]("https://wiki.ubuntu.com/Kernel/KernelBootParameters") page. When testing, make sure to try both your brightness keys and the xfce brightness plugin.

>  	
Re: xubuntu 12.10 brightness
i try with this

ls /sys/class/backlight

and show

acpi_video0 toshiba

after

sudo bash -c "echo 5 > /sys/class/backlight/acpi_video0/brightness"

but con toshiba dont work

and this work but i want use the brightness plugin for more confortabylity 

Which modules do you have loaded? The following command will list them:
```
lsmod
```

---

### Post by saiaN on 2013-01-23
thx for the explain , i will prove with this commands

and for lsmod the machine give me this

```
nightwing@nightwing:~$ lsmod
Module                  Size  Used by
snd_hda_codec_conexant    52203  1 
joydev                 17162  0 
kvm                   357807  0 
arc4                   12474  2 
snd_hda_intel          32516  4 
snd_hda_codec         111548  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13273  1 snd_hda_codec
snd_pcm                80235  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13133  0 
snd_rawmidi            25383  1 snd_seq_midi
microcode              18210  0 
snd_seq_midi_event     14476  1 snd_seq_midi
snd_seq                51281  2 snd_seq_midi,snd_seq_midi_event
psmouse                84878  0 
snd_timer              24412  2 snd_pcm,snd_seq
snd_seq_device         14138  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               71278  0 
videobuf2_core         32071  1 uvcvideo
videodev               95842  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12757  1 uvcvideo
videobuf2_memops       13213  1 videobuf2_vmalloc
snd                    62146  17 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
rtl8192ce              52880  0 
rtl8192c_common        47076  1 rtl8192ce
rtlwifi                64173  1 rtl8192ce
k10temp                12959  0 
mac80211              461203  3 rtl8192ce,rtl8192c_common,rtlwifi
serio_raw              13032  0 
soundcore              14600  1 snd
snd_page_alloc         14037  2 snd_hda_intel,snd_pcm
cfg80211              175574  2 rtlwifi,mac80211
i2c_piix4              12984  0 
radeon                820764  2 
toshiba_acpi           18239  0 
sparse_keymap          13659  1 toshiba_acpi
ttm                    75535  1 radeon
drm_kms_helper         47304  1 radeon
drm                   238811  4 radeon,ttm,drm_kms_helper
i2c_algo_bit           13198  1 radeon
wmi                    18591  1 toshiba_acpi
bnep                   17708  2 
rfcomm                 37277  0 
bluetooth             183270  10 bnep,rfcomm
parport_pc             31969  0 
ppdev                  12818  0 
binfmt_misc            17261  1 
mac_hid                13038  0 
video                  18848  0 
lp                     13300  0 
parport                40754  3 parport_pc,ppdev,lp
atl1c                  36176  0
```

---

### Post by Toz on 2013-01-23
I added code tags to your post above. Its easier to read screen output if you embed it in code tags. To do so, paste your code between **[noparse]```
 <your code here> 
```[/noparse]** tags.

---

### Post by Toz on 2013-01-23
I don't see the proprietary AMD driver running on this laptop (the radeon module is loaded). Can you post back the results of:
```
sudo lspci -vnn | grep -A12 VGA
```

---

### Post by saiaN on 2013-01-23
this give the command

```
   00:01.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI Wrestler [Radeon HD 6310] [1002:9802] (prog-if 00 [VGA controller])
    Subsystem: Toshiba America Info Systems Device [1179:fcd3]
    Flags: bus master, fast devsel, latency 0, IRQ 42
    Memory at 80000000 (32-bit, prefetchable) [size=256M]
    I/O ports at 4000 [size=256]
    Memory at 90300000 (32-bit, non-prefetchable) [size=256K]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Kernel driver in use: radeon
    Kernel modules: radeon
 
```

---

### Post by Toz on 2013-01-23
You are using the open source radeon driver. Start up Software Centre, select Edit->Sources and look on the Additional Drivers tab. Is the proprietary AMD driver listed?

Have you had any success with the kernel boot parameters?

---

### Post by saiaN on 2013-01-24
hi, i prove with the privative drives of amd and work, now i have more efficient in my notebook :)

thx for the help

---

