---
title: "No more sound on a Lenovo Thinkboot in Jammy"
date: 2022-09-14
forum: General Help
---

### Post by georgesgiralt on 2022-09-14
Hi Guys,
The culprit is a Lenovo Thinkbook Laptop (15G2 ITL) which has been upgraded to Jammy this week. 
I had perfect sound support on 20.04.5 LTS BEFORE upgrading. 
It worked for some time (do not know how long) and this morning, no more sound. 
I'm at sea and lost here. 
I've checked that the sound settings in parameters are not showing anything. I've tried to reinstall Alsa but to no avail. All packets are up to date. 
Could you please tell me what to check and how ? Because I can't understand what is needed and how to check if present/working. 
Many many thanks in advance for your help !

---

### Post by ActionParsnip on 2022-09-14
Please follow this
[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

Give the output of step 3 if you reach it.

---

### Post by georgesgiralt on 2022-09-14
Hello !
Thank you for your answer. 
I've followed the given procedure with a pinch of salt. 
For example, in step 1 I first checked the presence and status of packets *before* trying to install them.
and when I test for pulseaudio : 
```
$ pulseaudio --check
$ echo "$?"
0
$
```
Of course, still no joy, but the output of alsa-info is : 
alsa-info.txt.vuQq3DdZ5r (61,2 Ko) Plik  [https://plik.root.gg/file/ZZHFXeWLs8OpLlm8/Zw3QiwxLtzUj2d4E/alsa-info.txt.vuQq3DdZ5r](https://plik.root.gg/file/ZZHFXeWLs8OpLlm8/Zw3QiwxLtzUj2d4E/alsa-info.txt.vuQq3DdZ5r)
MAy I add that when I bought this machine, I needed to install oem packages :
```

ii  oem-sutton.simon-camille-meta         20.04ubuntu3           all          hardware support for Lenovo ThinkBook 14 G2 ITL, 15 G2 ITL
ii  oem-sutton.simon-factory-camille-meta 20.04ubuntu3           all          hardware support for Lenovo ThinkBook 14 G2 ITL, 15 G2 ITL (factory)
ii  oem-sutton.simon-factory-meta         4.0simon5              all          Meta package for the Sutton Simon image.
ii  oem-sutton.simon-meta                 4.0simon5              all          Meta package for the Sutton Simon image.

```
packages which are not available for Jammy. And I wonder if the problem does not lie there ? 
So All your help will be vastly appreciated !

---

### Post by #&amp;thj^% on 2022-09-14
Give this a try, not saying it will  work but changing from sof-hda-dsp to intel might work:
```
sudoedit /etc/default/grub
```
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash snd_hda_intel.dmic_detect=0"
```
update grub and reboot, now any better?
If not show this please:
```
**_lsmod | grep snd_**
####Mine as below:
snd_seq_dummy          16384  0
snd_hrtimer            16384  1
snd_seq               102400  7 snd_seq_dummy
snd_usb_audio         405504  4
snd_usbmidi_lib        49152  1 snd_usb_audio
snd_rawmidi            49152  1 snd_usbmidi_lib
snd_seq_device         16384  2 snd_seq,snd_rawmidi
snd_sof_amd_renoir     16384  0
snd_sof_amd_acp        49152  1 snd_sof_amd_renoir
snd_sof_pci            24576  1 snd_sof_amd_renoir
snd_sof               270336  3 snd_sof_amd_acp,snd_sof_pci,snd_sof_amd_renoir
snd_sof_utils          20480  1 snd_sof
snd_soc_core          417792  1 snd_sof
snd_compress           28672  1 snd_soc_core
ac97_bus               16384  1 snd_soc_core
snd_pcm_dmaengine      16384  1 snd_soc_core
snd_acp_pci            16384  0
snd_pci_acp6x          20480  0
snd_pci_acp5x          20480  0
snd_rn_pci_acp3x       24576  0
snd_acp_config         16384  3 snd_rn_pci_acp3x,snd_acp_pci,snd_sof_amd_renoir
mc                     77824  5 videodev,snd_usb_audio,videobuf2_v4l2,uvcvideo,videobuf2_common
snd_soc_acpi           16384  2 snd_acp_config,snd_sof_amd_renoir
snd_pci_acp3x          20480  0
snd_hda_codec_realtek   184320  1
snd_hda_codec_generic   114688  1 snd_hda_codec_realtek
ledtrig_audio          16384  1 snd_hda_codec_generic
snd_hda_codec_hdmi     90112  1
snd_hda_intel          61440  6
snd_intel_dspcfg       36864  1 snd_hda_intel
snd_intel_sdw_acpi     20480  1 snd_intel_dspcfg
snd_hda_codec         200704  4 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_realtek
snd_hda_core          122880  5 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek
snd_hwdep              20480  2 snd_usb_audio,snd_hda_codec
snd_pcm               180224  12 snd_sof_amd_acp,snd_hda_codec_hdmi,snd_pci_acp6x,snd_hda_intel,snd_usb_audio,snd_hda_codec,snd_sof,snd_compress,snd_soc_core,snd_sof_utils,snd_hda_core,snd_pcm_dmaengine
snd_timer              49152  3 snd_seq,snd_hrtimer,snd_pcm
snd                   135168  38 snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_usb_audio,snd_usbmidi_lib,snd_hda_codec,snd_hda_codec_realtek,snd_sof,snd_timer,snd_compress,snd_soc_core,snd_pcm,snd_rawmidi
soundcore              16384  1 snd


```

---

### Post by georgesgiralt on 2022-09-14
Thanks for your help. 
Alas, no joy ...
I had "GRUB_CMDLINE_LINUX_DEFAULT="acpi_osi=! \"acpi_osi=Windows 2018\"" " in my Grub default file. I can't remember why.  I switched to : GRUB_CMDLINE_LINUX_DEFAULT=snd_hda_intel.dmic_detect=0.
And the lsusb give : 
```
lsmod | grep snd
snd_hda_codec_hdmi     77824  1
snd_sof_pci_intel_tgl    16384  0
snd_sof_intel_hda_common   102400  1 snd_sof_pci_intel_tgl
soundwire_intel        40960  1 snd_sof_intel_hda_common
snd_sof_intel_hda      20480  1 snd_sof_intel_hda_common
snd_sof_pci            20480  2 snd_sof_intel_hda_common,snd_sof_pci_intel_tgl
snd_sof_xtensa_dsp     16384  1 snd_sof_intel_hda_common
snd_sof               147456  2 snd_sof_pci,snd_sof_intel_hda_common
snd_soc_hdac_hda       24576  1 snd_sof_intel_hda_common
snd_hda_ext_core       32768  3 snd_sof_intel_hda_common,snd_soc_hdac_hda,snd_sof_intel_hda
snd_soc_acpi_intel_match    61440  2 snd_sof_intel_hda_common,snd_sof_pci_intel_tgl
snd_soc_acpi           16384  2 snd_soc_acpi_intel_match,snd_sof_intel_hda_common
snd_hda_codec_realtek   159744  1
snd_hda_codec_generic   102400  1 snd_hda_codec_realtek
snd_soc_core          339968  4 soundwire_intel,snd_sof,snd_sof_intel_hda_common,snd_soc_hdac_hda
ledtrig_audio          16384  2 snd_hda_codec_generic,snd_sof
snd_compress           24576  1 snd_soc_core
ac97_bus               16384  1 snd_soc_core
snd_pcm_dmaengine      16384  1 snd_soc_core
snd_hda_intel          53248  0
snd_intel_dspcfg       28672  2 snd_hda_intel,snd_sof_intel_hda_common
snd_intel_sdw_acpi     20480  2 snd_sof_intel_hda_common,snd_intel_dspcfg
snd_hda_codec         163840  5 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_realtek,snd_soc_hdac_hda
snd_usb_audio         352256  0
snd_hda_core          110592  9 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_ext_core,snd_hda_codec,snd_hda_codec_realtek,snd_sof_intel_hda_common,snd_soc_hdac_hda,snd_sof_intel_hda
snd_usbmidi_lib        45056  1 snd_usb_audio
snd_hwdep              16384  2 snd_usb_audio,snd_hda_codec
snd_seq_midi           20480  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_seq                77824  2 snd_seq_midi,snd_seq_midi_event
snd_rawmidi            49152  2 snd_seq_midi,snd_usbmidi_lib
snd_pcm               143360  11 snd_hda_codec_hdmi,snd_hda_intel,snd_usb_audio,snd_hda_codec,soundwire_intel,snd_sof,snd_sof_intel_hda_common,snd_compress,snd_soc_core,snd_hda_core,snd_pcm_dmaengine
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
snd_timer              40960  2 snd_seq,snd_pcm
snd                   106496  15 snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_usb_audio,snd_usbmidi_lib,snd_hda_codec,snd_hda_codec_realtek,snd_timer,snd_compress,snd_soc_core,snd_pcm,snd_rawmidi
soundcore              16384  1 snd
mc                     65536  5 videodev,snd_usb_audio,videobuf2_v4l2,uvcvideo,videobuf2_common

```
I'm puzzled ! 
Never been a god in audio but, boy !

---

### Post by georgesgiralt on 2022-09-15
Update :
Today I downloaded the Jammy Jellyfish and make a bootable USB stick. I then booted on it and did all updates (to be in the "exact" same version on the live than in the laptop HD. 
I had sound right away in my live Jammy. 
As the boot parameters where only the standard default, I tried them on the HD Jammy on the laptop. Still no joy. The only speakers I see are the "dummy" one and, of course, no sound. 
I'm very very annoyed by this. It is starting to get on my nerves. 
Have a nice and bright day !

---

### Post by #&amp;thj^% on 2022-09-15
I know this both irritating and silly, but Run alsamixer and mute all the controls.
Unmute Master, Front and PCM and set their sliders to about 70% - Now test. 
That is if you haven't thrown in the towel. ;)
This isn't Ubuntu's fault totally, Everyone was ready to add wireplumber to the works but a last minute discussion and they pulled their original plan and stuck with Pipewire with Pulseaudio, so we're kind of left in a bit of a flux on some audio cards.

---

### Post by georgesgiralt on 2022-09-15
Well, nothing new. 
What puzzles me is that on Settings/sound, nothing's showing up. I've a "dummy output" and that's all .
I think I'm left with a comparison of the configuration in the live system and in the problematic one. 
Maybe I'll find something.

---

### Post by georgesgiralt on 2022-09-19
Hello,
Saturday was installation time on my laptop. 
I ended installing Jammy following a thread [https://ubuntuforums.org/showthread.php?t=2479159](https://ubuntuforums.org/showthread.php?t=2479159) ....
Then I spent a looong time reinstalling all the software I needed which was wiped off because of the installation. 
Now, I've got a running system with sound. 
There is still a problem : At boot the output is set to "AnalogOutput -- USB PnP Audio device" instead of the " Speaker  TigerLake LP Smart Sound Technology Audio Controler"... 
And that's annoying me ! 
I also miss the HDMI output in the settings. (Can't test using the HDMI output because I can't find an HDMI cable...)
So if you have a way to select the speakers automatically at boot/login, I'll be delighted to hear it ! 
Thanks a lot in advance for your help !

---

### Post by #&amp;thj^% on 2022-09-19
The simple workaround I found is adding the pactl set default sink command in startup applications.
[list]
    [*]Run: pactl list short sinks
    [*]Note the device name you want to use as default
    [*]Try to run: pactl set-default-sink <Your_Device_Name>[/list]
    This should work without giving you any error message.
First example on mine:
```
pactl list short sinks
53	alsa_output.pci-0000_05_00.6.pro-output-0	PipeWire	s32le 2ch 48000Hz	SUSPENDED

```
So if I set mine like:
```
pactl set-default-sink 'alsa_output.pci-0000_05_00.6.pro-output-0'
```
that device is now default.

---

### Post by georgesgiralt on 2022-09-19
Ah  !!! 
```
pactl list short sinks
1	alsa_output.pci-0000_00_1f.3-platform-skl_hda_dsp_generic.HiFi__hw_sofhdadsp_5__sink	module-alsa-card.c	s16le 2ch 48000Hz	SUSPENDED
2	alsa_output.pci-0000_00_1f.3-platform-skl_hda_dsp_generic.HiFi__hw_sofhdadsp_4__sink	module-alsa-card.c	s16le 2ch 48000Hz	SUSPENDED
3	alsa_output.pci-0000_00_1f.3-platform-skl_hda_dsp_generic.HiFi__hw_sofhdadsp_3__sink	module-alsa-card.c	s16le 2ch 48000Hz	SUSPENDED
4	alsa_output.pci-0000_00_1f.3-platform-skl_hda_dsp_generic.HiFi__hw_sofhdadsp__sink	module-alsa-card.c	s16le 2ch 48000Hz	SUSPENDED
5	alsa_output.usb-0c76_USB_PnP_Audio_Device-00.analog-stereo	module-alsa-card.c	s16le 2ch 48000Hz	SUSPENDED

```
The output of this command is written in undecipherable, language I do not possess.... I have a degree in esoteric and in burble but not in undecipherable. So I can't find my speakers in that list above ! 
The plot thickens....

---

### Post by #&amp;thj^% on 2022-09-19
> **georgesgiralt said:**
> Ah  !!! 
The output of this command is written in undecipherable, language I do not possess.... I have a degree in esoteric and in burble but not in undecipherable. So I can't find my speakers in that list above ! 
The plot thickens....
Stop It...:lolflag: If you make me laugh I'll blow-up and make a mistake...):P
You can set more than one device if you change devices a bit, IE:
```
sudo nano /etc/pulse/default.pa
```
and maybe add like this Example:
```

### Make some devices default
set-default-sink alsa_output.pci-0000_00_1f.3.analog-stereo
set-default-source alsa_output.pci-0000_00_1f.3.analog-stereo.monitor
```
Also make sure this line is commented out (#):
```
# load-module module-switch-on-connect
```
If I remember correctly when I last used Ubuntu I also removed " ~/.config/pulse "
Almost forgot the point here, these are your possibles:
```
1	alsa_output.pci-0000_00_1f.3-platform-skl_hda_dsp_generic.HiFi__hw_sofhdadsp_5__sink	
2	alsa_output.pci-0000_00_1f.3-platform-skl_hda_dsp_generic.HiFi__hw_sofhdadsp_4__sink	
3	alsa_output.pci-0000_00_1f.3-platform-skl_hda_dsp_generic.HiFi__hw_sofhdadsp_3__sink	
4	alsa_output.pci-0000_00_1f.3-platform-skl_hda_dsp_generic.HiFi__hw_sofhdadsp__sink	
```

---

### Post by georgesgiralt on 2022-09-19
So I did a bit of forensic search. 
IT appears that the USB devices are on an Thunderbolt dock (has an HDMI, jack and VGA output). 
Everything else is on the PCI TigerLake interface. 
So I unplugged the dock, removed the .config/pulse directory and selected the speakers and the microphone in the TigerLake interface (it was the sole line showing...) and found that the Gnome  preference created a .config/pulse directory with an "input" file and an "output" file. Alongside with a cookie file. 
And I guess I need a cookie myself...
Will see how the whole shebang behave tomorrow when I start it up .....
Thanks for your help !

---

### Post by #&amp;thj^% on 2022-09-19
> **georgesgiralt said:**
> So I did a bit of forensic search. 
 and found that the Gnome  preference created a .config/pulse directory with an "input" file and an "output" file. Alongside with a cookie file. 
And I guess I need a cookie myself...
Will see how the whole shebang behave tomorrow when I start it up .....
Thanks for your help !

Hmmm? so now that gets recreated in Gnome, Good Info thanks for that.
Keep us posted, and bring me a cookie as well next time, Chocolate Chip will work. ;)
EDIT: Memory Jog>>>"Thunderbolt Dock" Linux will default to a Dock and it's options, like Video/HDMI/VGA, Audio controls, I wish I had known this from the start, oh well I enjoy helping you regardless.
I also run a Docking device, to eliminate the sound fight I just Disable it in sound prefs.

---

### Post by georgesgiralt on 2022-09-20
Did not work. I had to switch to the speakers this morning... 
I'm starting to get annoyed by this thing....

---

### Post by #&amp;thj^% on 2022-09-20
If I was having this kind of problems with my Audio Devices on 22.04, but worked perfectly on 20.04, well I think we all know what I would do, but what will your choice be now?

As a tester I run into this as a constant, so my level of frustration has been defused. (Either it works or doesn't no more no less)
If your Dock was plugged in at boot, it auto defaults to that and all onboard hardware involved in the Dock.(Outside of Video/Display)

Audio on that laptop has issues past and present even in windows..[https://forums.lenovo.com/t5/ThinkBook-Notebooks/Lenovo-Thinkbook-15-IIL-Ubuntu-Linux-Driver-Issues/m-p/5030071](https://forums.lenovo.com/t5/ThinkBook-Notebooks/Lenovo-Thinkbook-15-IIL-Ubuntu-Linux-Driver-Issues/m-p/5030071)
and:[https://forums.lenovo.com/t5/ThinkBook-Notebooks/ThinkBook-15-G2-ITL-Audio-problem/m-p/5115950](https://forums.lenovo.com/t5/ThinkBook-Notebooks/ThinkBook-15-G2-ITL-Audio-problem/m-p/5115950)
Sorry your upgrade was less than satisfactory

---

### Post by georgesgiralt on 2022-09-20
Well, the ThinkBook 15 IIL is not the same hardware than mine and the second post seems to show that the drivers where not properly installed .... 
Lenovo has a reputation for broken ACPI tables and information. 
My laptop is a Compal one, with Insyde BIOS and even with the OEM Lenovo packets installed showed a huge amount of ACPI errors during boot up. 4
Before this one I had a Dell which did not work at all unless you installed the factory supplied Linux image and do not try to update any package.... Every update broke something. 
Actually the last laptop I had which ran flawlessly was my old Thinkpad E450 but it took ages to have it about fine. 
Computer makers are not interested by their product after they leave the factory. And they try (not very hard) to have them run under the current Windows OS and declare it perfect if the whole thing does not explode during boot up.... 
I _do_ hope we will have a standardized replacement for ACPI with proper specs and proper interface to pilot the more and more complicated hardware they put into our machines. 
(Initializing the Mobo of my very old Core 2 Duo machine take 1 second, the Thinkpad E450 is at 1.5 s and the thinkbook take more than 3 s... And the power of the hardware is many order faster than it was in the Core2 duo machine.... So we are not out of the woods.... And won't be. )

---

### Post by #&amp;thj^% on 2022-09-20
You picked up on main gist here: "ACPI errors" Lenovo has written for Windows on a lot of the newer Lappy's as of late, even mine:
```
inxi -SzAz
System:
  Kernel: 5.19.9-zen1-1-zen arch: x86_64 bits: 64 Desktop: Xfce v: 4.16.1
    Distro: Arch Linux
Audio:
  Device-1: NVIDIA driver: snd_hda_intel
  Device-2: AMD ACP/ACP3X/ACP6x Audio Coprocessor driver: N/A
  Device-3: AMD Family 17h/19h HD Audio driver: snd_hda_intel
  Device-4: DisplayLink UOEOS Laptop Dock type: USB
    driver: cdc_ncm,snd-usb-audio
  Sound Server-1: ALSA v: k5.19.9-zen1-1-zen running: yes
  Sound Server-2: PipeWire v: 0.3.58 running: yes
Machine:
  Type: Laptop System: LENOVO product: 82B5 v: Lenovo Legion 5 15ARH05
    serial: <superuser required>
  Mobo: LENOVO model: LNVNB161216 v: SDK0J40709 WIN
    serial: <superuser required> UEFI: LENOVO v: EUCN37WW date: 04/14/2022


```
When I first installed Linux on the above system, I had no touchpad, nor bluetooth, and WiFi
I have a deeper attachment to all hardware developers, reverse-engineering the endpoints that Lenovo (and other hardware manufacturers) have made available over the years. Because there is rarely any documentation provided by companies, it's up to a developer to look at the data in front of them and work out what various bits mean.
To me that sounds like a daunting task..;)
And yes I own a lot of Lenovo's devices,

---

