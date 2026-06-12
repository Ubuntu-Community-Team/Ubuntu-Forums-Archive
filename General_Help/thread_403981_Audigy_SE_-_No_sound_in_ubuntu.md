---
title: "Audigy SE - No sound in ubuntu"
date: 2007-04-07
forum: General Help
---

### Post by Salo on 2007-04-07
I have an creative audigy se sound card that just wont work in ubuntu 6.10

I have been through 2 dozen help files and how to's for checking that all the channels are unmuted, certain options are disabled, this and that are working. But again I have no sound.

I have no idea how to install and configure alsa...which may be the savior Im looking for.

Output of lsmod:

```
Module                  Size  Used by
wlan_tkip              13824  2 
ipv6                  272288  8 
binfmt_misc            13448  1 
rfcomm                 42260  0 
l2cap                  27136  5 rfcomm
bluetooth              53476  4 rfcomm,l2cap
fglrx                 548708  11 
speedstep_lib           5764  0 
cpufreq_userspace       5408  0 
cpufreq_stats           7744  0 
freq_table              6048  1 cpufreq_stats
cpufreq_powersave       2944  0 
cpufreq_ondemand        8876  0 
cpufreq_conservative     8712  0 
video                  17540  0 
tc1100_wmi              8324  0 
sbs                    16804  0 
sony_acpi               6412  0 
pcc_acpi               14080  0 
i2c_ec                  6272  1 sbs
i2c_core               23424  1 i2c_ec
hotkey                 11556  0 
dev_acpi               12292  0 
button                  7952  0 
battery                11652  0 
container               5632  0 
ac                      6788  0 
asus_acpi              17688  0 
af_packet              24584  4 
nls_utf8                3200  2 
ntfs                  112116  2 
fuse                   43912  0 
lp                     12964  0 
tsdev                   9152  0 
usbhid                 45152  0 
8139cp                 24832  0 
8139too                29056  0 
wlan_scan_sta          15744  1 
psmouse                41352  0 
mii                     6912  2 8139cp,8139too
serio_raw               8452  0 
ath_pci               100000  0 
ath_rate_sample        16512  1 ath_pci
wlan                  207708  5 wlan_tkip,wlan_scan_sta,ath_pci,ath_rate_sample
evdev                  11392  4 
ath_hal               192976  3 ath_pci,ath_rate_sample
pcspkr                  4352  0 
analog                 12960  0 
gameport               17160  1 analog
parport_pc             37796  1 
parport                39496  2 lp,parport_pc
intel_agp              26012  1 
agpgart                34888  2 fglrx,intel_agp
soundcore              11232  0 
floppy                 63044  0 
shpchp                 42144  0 
pci_hotplug            32828  1 shpchp
ext3                  142856  1 
jbd                    62228  1 ext3
ehci_hcd               34696  0 
uhci_hcd               24968  0 
usbcore               134912  4 usbhid,ehci_hcd,uhci_hcd
ide_generic             2432  0 
ata_piix               11780  0 
libata                 74892  1 ata_piix
scsi_mod              144648  1 libata
ide_cd                 33696  0 
cdrom                  38944  1 ide_cd
ide_disk               18560  5 
piix                   11780  1 
generic                 6276  0 
thermal                15624  0 
processor              31560  1 thermal
fan                     6020  0 
fbcon                  41504  0 
tileblit                3840  1 fbcon
font                    9344  1 fbcon
bitblit                 7168  1 fbcon
softcursor              3328  1 bitblit
vesafb                  9244  0 
capability              5896  0 
commoncap               8704  1 capability

```

Thanks.

---

### Post by Salo on 2007-04-07
bump

---

