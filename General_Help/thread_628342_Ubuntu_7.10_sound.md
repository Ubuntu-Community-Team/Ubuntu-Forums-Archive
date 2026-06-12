---
title: "Ubuntu 7.10 sound"
date: 2007-12-01
forum: General Help
---

### Post by gdr8205 on 2007-12-01
hi all,
im new to ubuntu and linux for that matter.  ive ran windows my whole life and never had a problem with sound. so im out of ideas on how to fix this.  ive lookd all over the internet to find solutions and they either dont work or the next program i add somehow makes it so theres no sound.ever.
umm the last thing i did was the switch to OSS from this [http://ubuntuforums.org/showpost.php?p=3768914&postcount=60](http://ubuntuforums.org/showpost.php?p=3768914&postcount=60).
it fixed my sound problem..but only with programs but when i go to you-tube or sumthing like that i get no sound.  then i read that OSS is really bad sound quality compared to ALSA.  so i was wondering if someone could help me get back Alsa and also get it working.

so based on other post u guys prolly need to c lspci which returns:



00:00.0 Host bridge: Intel Corporation 82925X/XE Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 82925X/XE PCI Express Root Port (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801FR/FRW (ICH6R/ICH6RW) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]
01:00.1 Display controller: ATI Technologies Inc RV370 [Radeon X300SE]
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)
04:00.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
04:01.0 Modem: Intel Corporation FA82537EP 56K V.92 Data/Fax Modem PCI (rev 04)
04:02.0 Multimedia audio controller: Creative Labs SB Audigy LS




and also might need lsmod  returns:

Module                  Size  Used by
ipv6                  273892  10 
af_packet              24840  4 
nls_iso8859_1           5120  1 
nls_cp437               6784  1 
vfat                   14080  1 
fat                    54300  1 vfat
isofs                  36412  0 
udf                    87204  1 
vmix                   14132  1 
ossusb                 56200  1 
ich                    20336  1 
audigyls               22384  3 
osscore               565812  4 vmix,ossusb,ich,audigyls
radeon                125472  2 
drm                    83348  3 radeon
agpgart                35016  1 drm
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ppdev                  10244  0 
speedstep_lib           6404  0 
cpufreq_ondemand        9612  0 
cpufreq_userspace       5280  0 
cpufreq_stats           7232  0 
freq_table              5792  2 cpufreq_ondemand,cpufreq_stats
cpufreq_powersave       2688  0 
cpufreq_conservative     8072  0 
button                  8976  0 
ac                      6148  0 
video                  18060  0 
dock                   10656  0 
container               5504  0 
sbs                    19592  0 
battery                11012  0 
lp                     12580  0 
arc4                    2944  2 
ecb                     4608  2 
blkcipher               7556  1 ecb
rc80211_simple          6912  1 
rt2500pci              19072  0 
rt2x00pci              11520  1 rt2500pci
rt2x00lib              19584  2 rt2500pci,rt2x00pci
rfkill                  8208  1 rt2x00lib
mac80211              171016  4 rc80211_simple,rt2500pci,rt2x00pci,rt2x00lib
cfg80211                7304  1 mac80211
xpad                    9988  0 
parport_pc             37412  1 
input_polldev           5896  1 rt2x00lib
crc_itu_t               3072  1 rt2x00lib
parport                37448  3 ppdev,lp,parport_pc
pcspkr                  4224  0 
eeprom_93cx6            3200  1 rt2500pci
ac97_bus                3200  0 
iTCO_wdt               11940  0 
iTCO_vendor_support     4868  1 iTCO_wdt
psmouse                39952  0 
serio_raw               8068  0 
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
evdev                  11136  3 
ext3                  133896  2 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0 
sd_mod                 30336  5 
sr_mod                 17828  1 
cdrom                  37536  1 sr_mod
ahci                   23300  0 
usbhid                 29536  0 
hid                    28928  1 usbhid
usb_storage            73024  2 
ide_core              116804  1 usb_storage
libusual               18448  1 usb_storage
tg3                   110980  0 
ata_piix               17540  2 
ata_generic             8452  0 
libata                125168  3 ahci,ata_piix,ata_generic
scsi_mod              147084  5 sg,sd_mod,sr_mod,usb_storage,libata
ehci_hcd               36492  0 
uhci_hcd               26640  0 
usbcore               138632  8 ossusb,xpad,usbhid,usb_storage,libusual,ehci_hcd,uhci_hcd
thermal                14344  0 
processor              32072  1 thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor


if someone could help me with this id really appreciate it.
thanks in advance,
Garrett

---

### Post by gdr8205 on 2007-12-01
and ive also seen this page [https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)
which makes absolutly no sense to me...

---

### Post by nnamdi on 2007-12-01
wats up

seems u got an intel sound card you could try this out an tell me wats up ok
[http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/](http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/)

reply your post when it gets fixed

---

### Post by gdr8205 on 2007-12-01
hey thanks for the really quick response.
although that didnt seem to fix my problem.

---

### Post by nnamdi on 2007-12-01
lspci -v | grep Audio
 then post the output ok

---

### Post by gdr8205 on 2007-12-01
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)

is the return

---

### Post by gdr8205 on 2007-12-01
any ideas?

---

### Post by gdr8205 on 2007-12-01
having no sound is getting annoying :/

---

### Post by gdr8205 on 2007-12-01
some please hlp me get alsa bak n workn please?

---

