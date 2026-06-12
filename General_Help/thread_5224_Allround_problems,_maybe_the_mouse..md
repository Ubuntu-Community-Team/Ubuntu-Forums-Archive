---
title: "Allround problems, maybe the mouse."
date: 2004-11-16
forum: General Help
---

### Post by ion on 2004-11-16
I've been having some weird problems since installing.

Every now and then, for no apparent reason, the mouse starts stuttering and lagging.
It seems to be the whole system though, but it's most visible through the mouse movement.
Animations and other things like that also lags, even though no process takes up any particular cpu power or memory.
Then it gets worse.
The system does one, some or all of the following:
* Incredible lag, nonresponsiveness of all input.
* The mouse pointer jumps around at random, even clicking and whatnot for no reason
* Starting the screensaver :-s
* Turning the screen black, and after X number of seconds "fades" back like it does from the screensaver.

Even though it's not a direct problem, it's still a bit funny.
Whenever I use a scrollbar or there's some graphical change onscreen, there's a light scraping noise in the speakers.
Should the graphics really influence the audio output? :-s

dmesg gives some error that says something about lost synchronisation, throwing away packets and errors in the pcmouse.c file
I'll try to get the output whenever the problem returns, but I had to reboot.

lspci says:
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 03)
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
0000:00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
0000:00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1a)
0000:00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1a)
0000:00:07.4 Bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
0000:00:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8029(AS)
0000:00:0b.0 Multimedia audio controller: Ensoniq ES1370 [AudioPCI]
0000:01:00.0 VGA compatible controller: nVidia Corporation NV25 [GeForce4 Ti 4200] (rev a3)

lsmod says:
Module                  Size  Used by
proc_intf               3968  0
cpufreq_powersave       2048  0
cpufreq_userspace       5336  0
freq_table              4356  0
button                  6936  0
ac                      5132  0
battery                 9740  0
ipv6                  230020  8
snd_ens1370            18788  4
snd_rawmidi            23232  1 snd_ens1370
snd_seq_device          7944  1 snd_rawmidi
snd_pcm_oss            48168  1
snd_mixer_oss          16640  3 snd_pcm_oss
snd_pcm                85540  2 snd_ens1370,snd_pcm_oss
snd_timer              23172  1 snd_pcm
snd_page_alloc         11144  2 snd_ens1370,snd_pcm
gameport                4736  1 snd_ens1370
snd_ak4531_codec        7680  1 snd_ens1370
snd                    50660  10 snd_ens1370,snd_rawmidi,snd_seq_device,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_ak4531_codec
soundcore               9824  4 snd
ne2k_pci                9312  0
8390                    9984  1 ne2k_pci
crc32                   4608  1 8390
uhci_hcd               29328  0
usbcore               104292  3 uhci_hcd
pci_hotplug            30640  0
via_agp                 8832  1
agpgart                31784  2 via_agp
floppy                 54996  0
pcspkr                  3816  0
rtc                    12216  0
md                     44744  0
dm_mod                 51068  1
capability              4872  0
commoncap               7168  1 capability
nvidia               4821428  12
parport_pc             32064  1
lp                     10436  0
parport                37320  2 parport_pc,lp
evdev                   9088  0
ide_cd                 38276  0
cdrom                  35872  1 ide_cd
tsdev                   7168  0
mousedev               10124  1
psmouse                17800  0
reiserfs              207600  2
ide_generic             1664  0
ide_disk               16768  6
via82cxxx              13084  1
ide_core              125272  4 ide_cd,ide_generic,ide_disk,via82cxxx
unix                   25904  782
fan                     4236  0
thermal                13200  0
processor              17712  1 thermal
font                    8576  0
vesafb                  6688  0
cfbcopyarea             3968  1 vesafb
cfbimgblt               3200  1 vesafb
cfbfillrect             3712  1 vesafb

---

### Post by cseefurth on 2004-11-27
[QUOTE=ion]Even though it's not a direct problem, it's still a bit funny.
Whenever I use a scrollbar or there's some graphical change onscreen, there's a light scraping noise in the speakers.
Should the graphics really influence the audio output? :-s
[/QUOTE]

Same here. Using the scrollbar causes a soft humming from my speakers.

Further details attached.

---

