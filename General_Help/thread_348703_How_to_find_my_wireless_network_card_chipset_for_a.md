---
title: "How to find my wireless network card chipset for aircrack"
date: 2007-01-29
forum: General Help
---

### Post by erugalatha on 2007-01-29
Hello,

I'm trying to find out my wireless network card name so I can know if I needto patch it or not for the madwifi drivers.

How do I do this?

Here's the output from lspci lsmod and iwconfig:

$ lsmod
Module                  Size  Used by
isofs                  37688  1
udf                    88580  0
nls_utf8                2176  1
ntfs                  103536  1
binfmt_misc            12296  1
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              50020  4 rfcomm,l2cap
ipt_limit               2432  8
iptable_mangle          2944  0
ipt_LOG                 6912  8
ipt_MASQUERADE          3456  0
ip_nat                 19628  1 ipt_MASQUERADE
ipt_TOS                 2560  0
ipt_REJECT              5632  1
ip_conntrack_irc        6768  0
ip_conntrack_ftp        7792  0
ipt_state               2048  6
ip_conntrack           51500  6 ipt_MASQUERADE,ip_nat,ip_conntrack_irc,ip_conntr ack_ftp,ipt_state
nfnetlink               6552  2 ip_nat,ip_conntrack
iptable_filter          3072  1
ip_tables              22400  8 ipt_limit,iptable_mangle,ipt_LOG,ipt_MASQUERADE, ipt_TOS,ipt_REJECT,ipt_state,iptable_filter
ppdev                   9220  0
fglrx                 388908  8
ipv6                  265856  6
speedstep_centrino      8400  1
cpufreq_userspace       4696  1
cpufreq_stats           5636  0
freq_table              4740  2 speedstep_centrino,cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        6428  0
cpufreq_conservative     7332  0
video                  16260  0
tc1100_wmi              6916  0
sony_acpi               5644  0
pcc_acpi               12416  0
hotkey                 11556  0
dev_acpi               11140  0
container               4608  0
button                  6672  0
acpi_sbs               19980  0
battery                 9988  1 acpi_sbs
ac                      5252  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
i2c_core               21904  1 i2c_acpi_ec
dm_mod                 58936  1
md_mod                 72532  0
sr_mod                 16932  0
sbp2                   24196  1
parport_pc             35780  0
lp                     11844  0
parport                36296  3 ppdev,parport_pc,lp
af_packet              22920  4
arc4                    2048  2
ieee80211_crypt_wep     5120  1
joydev                 10048  0
ipw3945               126620  1
ieee80211              37064  1 ipw3945
ieee80211_crypt         6272  2 ieee80211_crypt_wep,ieee80211
ieee80211_1_1_13       38216  0
ieee80211_1_1_13_crypt     6784  1 ieee80211_1_1_13
rtc                    13492  0
tsdev                   8000  0
snd_hda_intel          20504  4
snd_hda_codec         166448  1 snd_hda_intel
snd_pcm_oss            47648  0
snd_mixer_oss          18816  1 snd_pcm_oss
snd_pcm                81544  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
r1000                  16000  0
r8169                  28808  0
snd_timer              24964  2 snd_pcm
snd                    56804  12 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mix er_oss,snd_pcm,snd_timer
usbhid                 39904  0
psmouse                36100  0
serio_raw               7300  0
soundcore              10208  1 snd
snd_page_alloc         10760  2 snd_hda_intel,snd_pcm
intel_agp              22940  1
agpgart                34888  2 fglrx,intel_agp
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
sg                     37920  0
evdev                   9856  2
ext3                  135816  1
jbd                    58772  1 ext3
ide_generic             1536  0
ohci1394               35124  1
ieee1394              299832  2 sbp2,ohci1394
ehci_hcd               34184  0
uhci_hcd               33808  0
usbcore               130820  4 usbhid,ehci_hcd,uhci_hcd
sd_mod                 19984  5
ata_piix               11012  4
libata                 78992  1 ata_piix
scsi_mod              139496  5 sr_mod,sbp2,sg,sd_mod,libata
ide_cd                 33028  1
cdrom                  38560  2 sr_mod,ide_cd
piix                   11012  1
generic                 5124  0
thermal                13576  0
processor              23360  2 speedstep_centrino,thermal
fan                     4868  0
capability              5000  0
commoncap               7296  1 capability
vga16fb                13704  1
vgastate               10368  1 vga16fb
fbcon                  42784  72
tileblit                2816  1 fbcon
font                    8320  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2304  1 bitblit

$ lspci
0000:00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation Mobile PCI Express Graphics Port (rev 03)
0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
0000:00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
0000:00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
0000:00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
0000:00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
0000:00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
0000:00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
0000:00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
0000:00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
0000:00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
0000:00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controllers cc=IDE (rev 02)
0000:00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 7145
0000:04:00.0 Network controller: Intel Corporation: Unknown device 4222 (rev 02)
0000:05:04.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
0000:05:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"DBS Support"
          Mode:Managed  Frequency:2.442 GHz  Access Point: 00:0F:CC:99:09:0C
          Bit Rate:48 Mb/s   Tx-Power:15 dBm
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=95/100  Signal level=-29 dBm  Noise level=-30 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:389   Missed beacon:0

sit0      no wireless extensions.

---

### Post by majoridiot on 2007-01-29
> **erugalatha said:**
> 
0000:05:05.0 Ethernet controller: **Realtek** Semiconductor Co., Ltd. **RTL-8169** Gigabit Ethernet (rev 10)

:D

---

