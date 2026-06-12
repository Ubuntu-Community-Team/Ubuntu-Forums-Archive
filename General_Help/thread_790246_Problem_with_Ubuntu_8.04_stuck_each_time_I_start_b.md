---
title: "Problem with Ubuntu 8.04 stuck each time I start browsing the net."
date: 2008-05-11
forum: General Help
---

### Post by neuzen on 2008-05-11
Hi Everyone,

I recently purchased new computer and decided to try out Ubuntu 8.04.
After installing Ubuntu I try to surf the net for a while, after few minutes I encountered a problem:
It is as my computer was locked, I had no response from my keyboard or my mouse. The desktop didn't show any response, on the keyboard both the “caps lock” and “scroll lock” LEDs where permanently on (I searched the motherboard's user manual for any error description that could help me with no success).
Only after reset my computer started to response. Firstly I suspected that it was hardware problem but after short investigation I cam to conclude that it could be also driver or software problem since the computer was stuck only when I tried to invoke web browser (I tried out Firefox 3 beta, Firefox 2 and Galeon).

Few hardware details:
CPU: Intel core 2 duo E8200
Motherboard: Gigabyte GA-X48-DQ6
Memory: Kingston 2GB DDRII 800Mhz.
Disk: Western Digital 250G.
Video Card: Gigabyte 8400GS with 256MG GDDR2
Wireless Ethernet card: Edimax EW-7128G.

Few drivers details:
lsmod output:
Module Size Used by
ipv6 267780 10
af_packet 23812 5
rfcomm 41744 2
l2cap 25728 13 rfcomm
bluetooth 61156 4 rfcomm,l2cap
ppdev 10372 0
autofs4 23044 0
acpi_cpufreq 10796 0
cpufreq_ondemand 9740 2
cpufreq_powersave 2688 0
cpufreq_conservative 8712 0
cpufreq_userspace 5284 0
cpufreq_stats 7104 0
freq_table 5536 3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
video 19856 0
output 4736 1 video
container 5632 0
dock 11280 0
sbs 15112 0
sbshc 7680 1 sbs
battery 14212 0
iptable_filter 3840 0
ip_tables 14820 1 iptable_filter
x_tables 16132 1 ip_tables
ac 6916 0
sbp2 24072 0
lp 12324 0
arc4 2944 2
ecb 4480 2
blkcipher 8324 1 ecb
parport_pc 36260 1
parport 37832 3 ppdev,lp,parport_pc
rt61pci 25472 0
rt2x00pci 11264 1 rt61pci
rt2x00lib 22528 2 rt61pci,rt2x00pci
rfkill 8592 1 rt2x00lib
input_polldev 5896 1 rt2x00lib
serio_raw 7940 0
evdev 13056 3
pcspkr 4224 0
psmouse 40336 0
crc_itu_t 3072 1 rt2x00lib
mac80211 165652 3 rt61pci,rt2x00pci,rt2x00lib
cfg80211 15112 1 mac80211
nvidia 7825536 34
eeprom_93cx6 3200 1 rt61pci
iTCO_wdt 13092 0
snd_hda_intel 344728 4
iTCO_vendor_support 4868 1 iTCO_wdt
agpgart 34760 1 nvidia
snd_pcm_oss 42144 0
snd_mixer_oss 17920 1 snd_pcm_oss
i2c_core 24832 1 nvidia
snd_pcm 78596 2 snd_hda_intel,snd_pcm_oss
snd_page_alloc 11400 2 snd_hda_intel,snd_pcm
snd_hwdep 10500 1 snd_hda_intel
snd_seq_dummy 4868 0
snd_seq_oss 35584 0
snd_seq_midi 9376 0
snd_rawmidi 25760 1 snd_seq_midi
snd_seq_midi_event 8320 2 snd_seq_oss,snd_seq_midi
snd_seq 54224 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer 24836 2 snd_pcm,snd_seq
snd_seq_device 9612 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd 56996 19 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_ seq,snd_timer,snd_seq_device
button 9232 0
shpchp 34452 0
pci_hotplug 30880 1 shpchp
soundcore 8800 1 snd
ext3 136712 1
jbd 48404 1 ext3
mbcache 9600 1 ext3
sg 36880 0
sr_mod 17956 0
cdrom 37408 1 sr_mod
sd_mod 30720 3
pata_acpi 8320 0
ata_piix 19588 2
pata_jmicron 7040 0
ata_generic 8324 0
ahci 28420 0
libata 159344 5 pata_acpi,ata_piix,pata_jmicron,ata_generic,ahci
ohci1394 33584 0
scsi_mod 151436 5 sbp2,sg,sr_mod,sd_mod,libata
ieee1394 93752 2 sbp2,ohci1394
r8169 32900 0
ehci_hcd 37900 0
uhci_hcd 27024 0
usbcore 146028 3 ehci_hcd,uhci_hcd
thermal 16796 0
processor 36872 2 acpi_cpufreq,thermal
fan 5636 0
fbcon 42912 0
tileblit 3456 1 fbcon
font 9472 1 fbcon
bitblit 6784 1 fbcon
softcursor 3072 1 bitblit
fuse 50580 3


I would gladly appreciate any help:(,
Thanks in advance,
Neuzen

---

### Post by adityakavoor on 2008-05-11
update the latest xulrunner

You will be fine

```
sudo update-manager -d
```

---

### Post by neuzen on 2008-05-11
Hi,
Thank you for your reply,
I've tryed to do the command:
sudo update-manager -d

but, my system is up-to-date.
is there anything more I can do?

In addition I would like to clearify that I can surf the net with w3m from the console with no problem.
I've looked in syslog and didn't saw anything wird.


Thanks for the help,
Neuzen

---

