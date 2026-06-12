---
title: "Sound gone to crap?"
date: 2008-07-05
forum: General Help
---

### Post by Hashi on 2008-07-05
Hi,
  Just upgraded to 8.04, and the sound (in movies, mp3's etc) has gone all fuzzy and crappy. Do I have to install something else? It was beautiful in 7.10.
Jon

---

### Post by Gunman1982 on 2008-07-05
Uhm what changed ... wow ... uhm .. you got 7 spare days so I can tell you what changed from 7.10 to 8.04? I would just stick to the main stuff though ;). 

I guess the biggest thing what changed regarding sound was that now it defaults to the PulseAudio soundserver, which seems to give many users a headache, at least what I see from the posts. I don't use PulseAudio and since I don't know which hardware you use I can't recommend you to get rid of it and use alsa or oss.

To find out what card you have you can open a console and type in 'lspci' or 'lspci | grep audio' if you don't want such a big output.

---

### Post by Hashi on 2008-07-05
Thanks, Gunman
I tried what you suggested, and here is the output:

jon@jon-laptop:~$ lspci | grep audio
jon@jon-laptop:~$ lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 [Geforce 6150 Go] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
07:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
jon@jon-laptop:~$ 

As you can see, I got no output from the grep? What's the deal there I wonder?
I understand your comments about the new sound system, but can I do anything about it?
Ta, Jon

---

### Post by Gunman1982 on 2008-07-05
Well the grep is case sensitive and searched for 'audio' but it is ok, your soundcard still seems to be in the system:

00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)

Yes you can something about it, you can switch to a different kind. But that may be not that easy.

I'm not really familiar with this card so I can't really suggest you an easy way to solve the problems you have. Maybe you can give the outputs of 'lsof | grep snd' and 'cat /proc/modules'?

---

### Post by Hashi on 2008-07-05
Sure thing, here it is:

jon@jon-laptop:~$ lspci | grep audio
jon@jon-laptop:~$ lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 [Geforce 6150 Go] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
07:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
jon@jon-laptop:~$ clear

jon@jon-laptop:~$ lsof | grep snd
mixer_app 5965        jon   19u      CHR      116,0              11852 /dev/snd/controlC0
gconf-hel 6017        jon  mem       REG        8,1   357520   7014539 /usr/lib/libsndfile.so.1.0.17
jon@jon-laptop:~$ cat /proc/modules
ipv6 267780 10 - Live 0xf8e2f000
vmnet 38828 13 - Live 0xf8d96000 (P)
vmmon 113388 0 - Live 0xf8e12000 (P)
af_packet 23812 2 - Live 0xf8d8f000
rfcomm 41744 2 - Live 0xf8b41000
l2cap 25728 13 rfcomm, Live 0xf8b26000
bluetooth 61156 4 rfcomm,l2cap, Live 0xf8b31000
ppdev 10372 0 - Live 0xf8b11000
powernow_k8 16704 1 - Live 0xf8b17000
cpufreq_userspace 5284 0 - Live 0xf8b0e000
cpufreq_conservative 8712 0 - Live 0xf8b0a000
cpufreq_powersave 2688 0 - Live 0xf887c000
cpufreq_ondemand 9740 1 - Live 0xf8ac7000
cpufreq_stats 7104 0 - Live 0xf8b02000
freq_table 5536 3 powernow_k8,cpufreq_ondemand,cpufreq_stats, Live 0xf8afa000
container 5632 0 - Live 0xf8af7000
dock 11280 0 - Live 0xf8a89000
sbs 15112 0 - Live 0xf8afd000
sbshc 7680 1 sbs, Live 0xf8ac4000
iptable_filter 3840 0 - Live 0xf8848000
ip_tables 14820 1 iptable_filter, Live 0xf8af2000
x_tables 16132 1 ip_tables, Live 0xf8acb000
sbp2 24072 0 - Live 0xf8a97000
parport_pc 36260 0 - Live 0xf8ae8000
lp 12324 0 - Live 0xf8aa9000
parport 37832 3 ppdev,parport_pc,lp, Live 0xf8add000
joydev 13120 0 - Live 0xf8aa4000
snd_hda_intel 344728 2 - Live 0xf8b4d000
snd_pcm_oss 42144 0 - Live 0xf8ad1000
snd_mixer_oss 17920 1 snd_pcm_oss, Live 0xf8a9e000
snd_pcm 78596 2 snd_hda_intel,snd_pcm_oss, Live 0xf8aaf000
snd_page_alloc 11400 2 snd_hda_intel,snd_pcm, Live 0xf8a85000
snd_hwdep 10500 1 snd_hda_intel, Live 0xf89e0000
snd_seq_dummy 4868 0 - Live 0xf8a4b000
snd_seq_oss 35584 0 - Live 0xf8a8d000
snd_seq_midi 9376 0 - Live 0xf8a7c000
snd_rawmidi 25760 1 snd_seq_midi, Live 0xf8a6e000
snd_seq_midi_event 8320 2 snd_seq_oss,snd_seq_midi, Live 0xf8a5a000
video 19856 0 - Live 0xf8a76000
output 4736 1 video, Live 0xf8a50000
sdhci 19076 0 - Live 0xf8a54000
snd_seq 54224 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event, Live 0xf8a5f000
serio_raw 7940 0 - Live 0xf8a48000
ricoh_mmc 4352 0 - Live 0xf8a45000
mmc_core 51460 1 sdhci, Live 0xf8a15000
snd_timer 24836 2 snd_pcm,snd_seq, Live 0xf8a3d000
snd_seq_device 9612 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq, Live 0xf8a11000
psmouse 40336 0 - Live 0xf8a32000
wmi_acer 9644 0 - Live 0xf8882000
i2c_nforce2 7680 0 - Live 0xf89ac000
ac 6916 0 - Live 0xf89a9000
battery 14212 0 - Live 0xf89d8000
snd 56996 15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device, Live 0xf8a23000
button 9232 0 - Live 0xf899f000
agpgart 34760 0 - Live 0xf8a07000
k8temp 6656 0 - Live 0xf8975000
shpchp 34452 0 - Live 0xf89c4000
pci_hotplug 30880 1 shpchp, Live 0xf89cf000
evdev 13056 8 - Live 0xf89a4000
i2c_core 24832 1 i2c_nforce2, Live 0xf89bc000
soundcore 8800 1 snd, Live 0xf88d0000
pcspkr 4224 0 - Live 0xf88cd000
ext3 136712 1 - Live 0xf89e4000
jbd 48404 1 ext3, Live 0xf89af000
mbcache 9600 1 ext3, Live 0xf8829000
sg 36880 0 - Live 0xf88e8000
sr_mod 17956 0 - Live 0xf88e2000
cdrom 37408 1 sr_mod, Live 0xf8994000
sd_mod 30720 3 - Live 0xf898b000
usbhid 31872 0 - Live 0xf896c000
hid 38784 1 usbhid, Live 0xf8961000
usb_storage 73664 0 - Live 0xf8978000
libusual 19108 1 usb_storage, Live 0xf8891000
sata_nv 27528 2 - Live 0xf8959000
pata_amd 14212 0 - Live 0xf8897000
ohci1394 33584 0 - Live 0xf88c3000
forcedeth 51980 0 - Live 0xf88d4000
pata_acpi 8320 0 - Live 0xf887e000
ieee1394 93752 2 sbp2,ohci1394, Live 0xf8941000
ata_generic 8324 0 - Live 0xf8860000
libata 159344 4 sata_nv,pata_amd,pata_acpi,ata_generic, Live 0xf8919000
scsi_mod 151436 6 sbp2,sg,sr_mod,sd_mod,usb_storage,libata, Live 0xf88f3000
ehci_hcd 37900 0 - Live 0xf8886000
ohci_hcd 25348 0 - Live 0xf8872000
usbcore 146028 6 usbhid,usb_storage,libusual,ehci_hcd,ohci_hcd, Live 0xf889e000
thermal 16796 0 - Live 0xf885a000
processor 36872 2 powernow_k8,thermal, Live 0xf8867000
fan 5636 0 - Live 0xf8842000
fbcon 42912 0 - Live 0xf884e000
tileblit 3456 1 fbcon, Live 0xf8831000
font 9472 1 fbcon, Live 0xf882d000
bitblit 6784 1 fbcon, Live 0xf8824000
softcursor 3072 1 bitblit, Live 0xf8827000
fuse 50580 1 - Live 0xf8834000
jon@jon-laptop:~$ 

Thanks for your help, I really mean it.
Jon

---

### Post by Gunman1982 on 2008-07-05
Ok now its the point where I start guessing stuff because I have neither PulseAudio nor such a soundcard.

If you use xmms or amarok or whatever program to play music try to change the output to alsa and check if that helps.

---

### Post by Hashi on 2008-07-05
Will do. I actually use Banshee, but I can try other progs. The thing is, I notice this distortion when playing videos using VLC. I think it is an 'across the board' problem, but I will try some music via various players and see what happens,
Many thanks,
Jon

---

### Post by Gunman1982 on 2008-07-05
Oh can change the audio module in vlc too. Open vlc, click on Properties->properties. Then choose Audio and tick the small box in the lower right corner 'extended options' You should get a dropdown on the right side there you choose alsa. And then test it.

Oh and maybe this whole discussion shoud moved into the Multimedia part of this forum.
There is one sticky about problems with sound already [http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449") I guess you should look into it.

---

### Post by Hashi on 2008-07-05
Hi again. Just downloaded Amarok and xmms. Tried both. and the sound is seriously cr*p. I mean, totally unlistenable. It's like total distortion, no matter which player I use. I know my hardware is OK. this only happened since I updated to 8.04. Is there some way I can get rid of Pulse Audio?
Thanks Jon.

---

### Post by Anzan on 2008-07-05
GUI:

System/Preferences/Sound

and choose ALSA for all events listed.

---

### Post by chrisccoulson on 2008-07-05
This might seem really obvious, but have you tried turning the master volume down to, say, 80%? I would also open the main volume control and turn the PCM channel down to 80% too. My sound clips and distorts at 100%

---

### Post by michaelzap on 2008-07-05
There are quite a lot of threads on this already if you search for them, including this one:
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by Topsiho on 2008-07-05
In page

[https://lists.ubuntu.com/archives/ubuntu-announce/2008-July/000112.html](https://lists.ubuntu.com/archives/ubuntu-announce/2008-July/000112.html)

I read

[I]"While we have fixed a number of audio-related issues, including a
scheduler problem that caused audio stuttering under load (#188226), other
audio playback problems may still exist, because so far we have been
unable to verify a targeted fix that does not cause regressions for other
users. We will continue to investigate this, and would welcome people with
problems to provide feedback on Luke Yelavich's test packages.  See
[https://bugs.launchpad.net/bugs/191027](https://bugs.launchpad.net/bugs/191027) for details."[/I]

so it is a known problem with Hardy. See also the Launchpad page and possibly you can add your feedback to the discussion there and help fix it :)

Topsiho

---

### Post by wdaniels on 2008-07-05
> **chrisccoulson said:**
> This might seem really obvious, but have you tried turning the master volume down to, say, 80%? I would also open the main volume control and turn the PCM channel down to 80% too. My sound clips and distorts at 100%

It does seem obvious, but it's where I'd put my money for this one. I have the same audio chipset and I used to have trouble with getting the volume to a reasonable (i.e. loud ;)) level, then with Hardy it magically got fixed. So if you've got everything turned up to full (maybe even pre-amp in an equalizer like I was doing) that could be why it's all distorted now.

---

### Post by LinuxRocks713 on 2008-07-05
> **Hashi said:**
> Hi,
  Just upgraded to 8.04, and the sound (in movies, mp3's etc) has gone all fuzzy and crappy. Do I have to install something else? It was beautiful in 7.10.
Jon

From: [https://wiki.ubuntu.com/EasyCodecInstallation](https://wiki.ubuntu.com/EasyCodecInstallation)

```

sudo apt-get install gstreamer0.10-esd gstreamer0.10-plugins-base gstreamer0.10-plugins-farsight gstreamer0.10-plugins-good gstreamer0.10-alsa gstreamer0.10-sdl gstreamer0.10-plugins-bad gstreamer0.10-gl gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-gnomevfs gstreamer0.10-x gstreamer0.10-plugins-ugly gstreamer0.10-ffmpeg

```

---

### Post by Genecks on 2008-07-06
Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)

I can confirm this is a bug in Ubuntu 8.04 (as of a total dist-upgrade on July 5th), or a lack of knowledge on the developers to correctly setup modules in the freaking kernel that was in the last release. I'm really starting to believe the devs are incompetent.

I'm not the only one having this issue. So far, it seems like three people are having it with Hardy Heron.

This is one other person.
[http://ubuntuforums.org/showthread.php?t=772258](http://ubuntuforums.org/showthread.php?t=772258)

Here are some command outputs:

> lspci

00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 [GeForce 6150 LE] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:0a.0 Communication controller: Conexant HSF 56k Data/Fax Modem

> workstation@universe:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

> workstation@universe:~$ lspci -v

00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
	Subsystem: Hewlett-Packard Company Unknown device 2a45
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
	Subsystem: Hewlett-Packard Company Unknown device 2a45
	Flags: 66MHz, fast devsel

00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
	Subsystem: Hewlett-Packard Company Unknown device 2a45
	Flags: 66MHz, fast devsel

00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
	Subsystem: Hewlett-Packard Company Unknown device 2a45
	Flags: 66MHz, fast devsel

00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
	Subsystem: Hewlett-Packard Company Unknown device 2a45
	Flags: bus master, 66MHz, fast devsel, latency 0

00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
	Subsystem: Hewlett-Packard Company Unknown device 2a45
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
	Subsystem: Hewlett-Packard Company Unknown device 2a45
	Flags: 66MHz, fast devsel

00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
	Subsystem: Hewlett-Packard Company Unknown device 2a45
	Flags: 66MHz, fast devsel

00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000b000-0000bfff
	Memory behind bridge: fde00000-fdefffff
	Prefetchable memory behind bridge: 00000000fdb00000-00000000fdbfffff
	Capabilities: <access denied>

00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: fda00000-fdafffff
	Prefetchable memory behind bridge: 00000000fd900000-00000000fd9fffff
	Capabilities: <access denied>

00:05.0 VGA compatible controller: nVidia Corporation C51 [GeForce 6150 LE] (rev a2) (prog-if 00 [VGA controller])
	Subsystem: Hewlett-Packard Company Unknown device 2a45
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
	Memory at fc000000 (32-bit, non-prefetchable) [size=16M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Memory at fb000000 (64-bit, non-prefetchable) [size=16M]
	[virtual] Expansion ROM at 88000000 [disabled] [size=128K]
	Capabilities: <access denied>

00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
	Subsystem: Hewlett-Packard Company Unknown device 2a45
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
	Subsystem: Hewlett-Packard Company Unknown device 2a45
	Flags: bus master, 66MHz, fast devsel, latency 0

00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
	Subsystem: Hewlett-Packard Company Unknown device 2a45
	Flags: 66MHz, fast devsel, IRQ 255
	I/O ports at 4c00 [size=64]
	I/O ports at 4c40 [size=64]
	Capabilities: <access denied>

00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
	Subsystem: Hewlett-Packard Company Unknown device 2a45
	Flags: 66MHz, fast devsel

00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) (prog-if 10 [OHCI])
	Subsystem: Hewlett-Packard Company Unknown device 2a45
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
	Memory at fe02f000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Unknown device 2a45
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
	Memory at fe02e000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1) (prog-if 8a [Master SecP PriP])
	Subsystem: Unknown device f03c:2a45
	Flags: bus master, 66MHz, fast devsel, latency 0
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at f400 [size=16]
	Capabilities: <access denied>

00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1) (prog-if 85 [Master SecO PriO])
	Subsystem: Hewlett-Packard Company Unknown device 2a45
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 19
	I/O ports at 09f0 [size=8]
	I/O ports at 0bf0 [size=4]
	I/O ports at 0970 [size=8]
	I/O ports at 0b70 [size=4]
	I/O ports at e000 [size=16]
	Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1) (prog-if 85 [Master SecO PriO])
	Subsystem: Hewlett-Packard Company Unknown device 2a45
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
	I/O ports at 09e0 [size=8]
	I/O ports at 0be0 [size=4]
	I/O ports at 0960 [size=8]
	I/O ports at 0b60 [size=4]
	I/O ports at cc00 [size=16]
	Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2) (prog-if 01 [Subtractive decode])
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=128
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: fdd00000-fddfffff
	Prefetchable memory behind bridge: fdc00000-fdcfffff
	Capabilities: <access denied>

00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
	Subsystem: Hewlett-Packard Company Unknown device 2a45
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
	Memory at fe024000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
	Subsystem: Hewlett-Packard Company Unknown device 2a45
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18
	Memory at fe02b000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at c800 [size=8]
	Capabilities: <access denied>

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
	Flags: fast devsel
	Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
	Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	Flags: fast devsel
	Capabilities: <access denied>

03:0a.0 Communication controller: Conexant HSF 56k Data/Fax Modem
	Subsystem: Conexant Unknown device 200c
	Flags: bus master, medium devsel, latency 32, IRQ 255
	Memory at fddf0000 (32-bit, non-prefetchable) [size=64K]
	I/O ports at ac00 [size=8]
	Capabilities: <access denied>

> 
[http://www.alsa-project.org/main/index.php/Matrix:Vendor-Nvidia](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Nvidia)

---

