---
title: "Need help fixing sound after upgrade to Heron"
date: 2008-04-26
forum: General Help
---

### Post by Vexxon on 2008-04-26
**Edit: Fixed the problem, see second post for details**

So I just upgraded to Heron and have been trying to get my sound to work for the past 8 hours or so. I remember my sound breaking when I upgraded to Gutsy Gibbon, too, but I don't remember how I fixed it. >.>

The odd thing is, I get no sound when I plug my speakers into the place on my sound card that I normally plug them into (the green hole), but I get a static-overlayed sound (I can hear the actual sounds through it) coming only from my left speaker when I plug it into the blue port (not sure what its actual name is).

I've gone through everything in this general solutions guide, to no avail:
[http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound](http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound)

I use an audigy LS card (I believe that's what its called).

output of lspci:
00:00.0 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:09.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
**00:0a.0 Multimedia audio controller: Creative Labs SB Audigy LS**
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: nVidia Corporation NV20 [GeForce3 Ti 200] (rev a3)

output of lsmod:
Module                  Size  Used by
ipv6                  267780  8 
binfmt_misc            12808  1 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0 
speedstep_lib           6532  0 
cpufreq_userspace       5284  0 
cpufreq_stats           7104  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9740  0 
freq_table              5536  2 cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     8712  0 
video                  19856  0 
output                  4736  1 video
sbs                    15112  0 
sbshc                   7680  1 sbs
dock                   11280  0 
container               5632  0 
ac                      6916  0 
battery                14212  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
af_packet              23812  2 
aes_i586               33536  0 
dm_crypt               15364  0 
dm_mod                 62660  1 dm_crypt
lp                     12324  0 
wlan_wep                8064  1 
wlan_scan_sta          14720  1 
ath_rate_sample        14336  1 
lmpcm_usb               7168  0 
snd_ca0106             36960  3 
snd_ac97_codec        102180  1 snd_ca0106
snd_pcm_oss            51232  0 
snd_pcm                86660  4 snd_ca0106,snd_ac97_codec,snd_pcm_oss
snd_mixer_oss          18432  1 snd_pcm_oss
snd_seq_dummy           4996  0 
snd_seq_oss            35968  0 
evdev                  13056  4 
nvidia               4718832  32 
snd_seq_midi           10784  0 
snd_rawmidi            27168  2 snd_ca0106,snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                58320  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              25988  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
button                  9232  0 
i2c_viapro              9876  0 
snd                    64708  18 snd_ca0106,snd_ac97_codec,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq_midi_event,snd_seq,snd_timer,snd_seq_device
ath_pci               101024  0 
via_agp                11136  1 
agpgart                34760  2 nvidia,via_agp
parport_pc             36260  1 
parport                37832  3 ppdev,lp,parport_pc
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
i2c_core               24832  2 nvidia,i2c_viapro
ac97_bus                3200  1 snd_ac97_codec
soundcore               8800  1 snd
snd_page_alloc         12168  2 snd_ca0106,snd_pcm
wlan                  207728  5 wlan_wep,wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               192592  3 ath_rate_sample,ath_pci
pcspkr                  4224  0 
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
usbhid                 31872  0 
hid                    38784  1 usbhid
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sd_mod                 30720  3 
sata_via               12420  0 
pata_via               13316  2 
floppy                 59588  0 
ehci_hcd               37900  0 
pata_acpi               8320  0 
uhci_hcd               27024  0 
ata_generic             8324  0 
via_rhine              26632  0 
mii                     6400  1 via_rhine
usbcore               146028  5 lmpcm_usb,usbhid,ehci_hcd,uhci_hcd
libata                159344  4 sata_via,pata_via,pata_acpi,ata_generic
scsi_mod              151436  4 sg,sr_mod,sd_mod,libata
thermal                16796  0 
processor              36872  1 thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  3 

I'm not entirely sure if I have the right driver, or if I've configured it correctly in ALSA. How would I check this? I believe the driver I'm supposed to be using is the ca0106 driver.

Any help would be greatly appreciated.

---

### Post by Vexxon on 2008-04-26
Edit: Nevermind, I fixed it!:guitar:

Ended up doing: sudo gedit ~/.asoundrc

Then replacing the file with the one in the first post of this thread: [http://ubuntuforums.org/showthread.php?p=1269056#post1269056](http://ubuntuforums.org/showthread.php?p=1269056#post1269056)

Then double clicked my volume control icon and went to edit>preferences, and clicked on everything I could checkmark.

Then went to the new "switches" tab and unchecked IEC958, and it worked!

---

