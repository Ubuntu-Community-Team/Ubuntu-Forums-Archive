---
title: "dmesg errors when plugging in usb 2.0 HD"
date: 2005-08-09
forum: General Help
---

### Post by halo five on 2005-08-09
Hi all,

USB 2.0 external HD, formatted FAT, powered up and plugged into my Ubuntu desktop and BOOM, dmesg tells me(Excerpt):

[FONT=Courier New]USB Mass Storage support registered.
usb-storage: device found at 2
usb-storage: waiting for device to settle before scanning
  Vendor: Apple     Model: iPod              Rev: 1.62
  Type:   Direct-Access                      ANSI SCSI revision: 00
usb-storage: device scan complete
SCSI device sda: 39063023 512-byte hdwr sectors (20000 MB)
sda: Write Protect is off
sda: Mode Sense: 64 00 00 08
sda: assuming drive cache: write through
SCSI device sda: 39063023 512-byte hdwr sectors (20000 MB)
sda: Write Protect is off
sda: Mode Sense: 64 00 00 08
sda: assuming drive cache: write through
 /dev/scsi/host0/bus0/target0/lun0: p1 p2
Attached scsi removable disk sda at scsi0, channel 0, id 0, lun 0
FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
FAT: Filesystem panic (dev sda2)
    fat_bmap_cluster: request beyond EOF (i_pos 1218947)
    File system has been set read-only
FAT: Filesystem panic (dev sda2)
    fat_bmap_cluster: request beyond EOF (i_pos 1218947)
FAT: Filesystem panic (dev sda2)
    fat_bmap_cluster: request beyond EOF (i_pos 1218947)
FAT: Filesystem panic (dev sda2)
    fat_bmap_cluster: request beyond EOF (i_pos 1218947)
FAT: Filesystem panic (dev sda2)
    fat_bmap_cluster: request beyond EOF (i_pos 1218947)
FAT: Filesystem panic (dev sda2)
    fat_bmap_cluster: request beyond EOF (i_pos 1218947)
FAT: Filesystem panic (dev sda2)
    fat_bmap_cluster: request beyond EOF (i_pos 1218947)
FAT: Filesystem panic (dev sda2)
    fat_bmap_cluster: request beyond EOF (i_pos 1218947)
FAT: Filesystem panic (dev sda2)
    fat_bmap_cluster: request beyond EOF (i_pos 1218947)
FAT: Filesystem panic (dev sda2)
    fat_bmap_cluster: request beyond EOF (i_pos 1218947)
FAT: Filesystem panic (dev sda2)
    fat_bmap_cluster: request beyond EOF (i_pos 1218947)
FAT: Filesystem panic (dev sda2)
    fat_bmap_cluster: request beyond EOF (i_pos 1218947)
FAT: Filesystem panic (dev sda2)
    fat_bmap_cluster: request beyond EOF (i_pos 1218947)
FAT: Filesystem panic (dev sda2)
    fat_bmap_cluster: request beyond EOF (i_pos 1218947)
FAT: Filesystem panic (dev sda2)
    fat_bmap_cluster: request beyond EOF (i_pos 1218947)
FAT: Filesystem panic (dev sda2)
    fat_bmap_cluster: request beyond EOF (i_pos 1218947)
FAT: Filesystem panic (dev sda2)
    fat_bmap_cluster: request beyond EOF (i_pos 1218947)
FAT: Filesystem panic (dev sda2)
    fat_bmap_cluster: request beyond EOF (i_pos 1218947)
FAT: Filesystem panic (dev sda2)
    fat_bmap_cluster: request beyond EOF (i_pos 1218947)
FAT: Filesystem panic (dev sda2)
    fat_bmap_cluster: request beyond EOF (i_pos 1218947)
FAT: Filesystem panic (dev sda2)
    fat_bmap_cluster: request beyond EOF (i_pos 1218947)
FAT: Filesystem panic (dev sda2)
    fat_bmap_cluster: request beyond EOF (i_pos 1218947)
FAT: Filesystem panic (dev sda2)
    fat_bmap_cluster: request beyond EOF (i_pos 1218947)
FAT: Filesystem panic (dev sda2)
    fat_bmap_cluster: request beyond EOF (i_pos 1218947)
FAT: Filesystem panic (dev sda2)
    fat_bmap_cluster: request beyond EOF (i_pos 1218947)
FAT: Filesystem panic (dev sda2)
    fat_bmap_cluster: request beyond EOF (i_pos 1218947)
FAT: Filesystem panic (dev sda2)
    fat_bmap_cluster: request beyond EOF (i_pos 1218947)
FAT: Filesystem panic (dev sda2)
    fat_bmap_cluster: request beyond EOF (i_pos 1218947)
FAT: Filesystem panic (dev sda2)
    fat_bmap_cluster: request beyond EOF (i_pos 1218947)
program gtkpod is using a deprecated SCSI ioctl, please convert it to SG_IO
usb 4-4: USB disconnect, address 2
scsi0 (0:0): rejecting I/O to dead device
SCSI error: host 0 id 0 lun 0 return code = 4000000
        Sense class 0, sense error 0, extended sense 0
will@kain:~$ 5~
[/FONT]

Nice, eh?  Not sure about the iPod messages, I had previously had an iPod connected, maybe it thinks it's still trying to connect to the 20GB iPod, and is barfing because it finds an 80GB FAT formatted hard drive?

Anyway, any help appreciated.  I'm kind of new.  Output from lsmod:
[FONT=Courier New]
will@kain:~$ lsmod
Module                  Size  Used by
nls_utf8                2176  0
nls_cp437               5888  0
vfat                   12928  0
fat                    37792  1 vfat
sd_mod                 16784  0
usb_storage            64064  0
scsi_mod              119936  2 sd_mod,usb_storage
ppp_mppe               12928  0
ppp_async              10752  0
crc_ccitt               2176  1 ppp_async
ppp_generic            27668  2 ppp_mppe,ppp_async
slhc                    7040  1 ppp_generic
proc_intf               4100  0
freq_table              4100  0
cpufreq_userspace       4572  0
cpufreq_ondemand        6172  0
cpufreq_powersave       1920  0
radeon                 69760  1
drm                    59412  2 radeon
video                  16260  0
sony_acpi               6280  0
pcc_acpi               11264  0
button                  6800  0
battery                10244  0
container               4608  0
ac                      4996  0
ipv6                  229504  40
af_packet              20744  2
8139too                24320  0
mii                     4736  1 8139too
snd_cmipci             29472  2
snd_pcm_oss            47652  1
snd_mixer_oss          16768  2 snd_pcm_oss
snd_pcm                84872  2 snd_cmipci,snd_pcm_oss
snd_page_alloc          9604  1 snd_pcm
snd_opl3_lib           10112  1 snd_cmipci
snd_timer              23300  2 snd_pcm,snd_opl3_lib
snd_hwdep               9220  1 snd_opl3_lib
gameport                4608  1 snd_cmipci
snd_mpu401_uart         7168  1 snd_cmipci
snd_rawmidi            22944  1 snd_mpu401_uart
snd_seq_device          8332  2 snd_opl3_lib,snd_rawmidi
snd                    50276  10 snd_cmipci,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_opl3_lib,snd_timer,snd_hwdep,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               9824  3 snd
i2c_i801                8076  0
i2c_core               21264  1 i2c_i801
ehci_hcd               29444  0
uhci_hcd               30224  0
usbcore               107384  4 usb_storage,ehci_hcd,uhci_hcd
pci_hotplug            30512  0
intel_agp              20636  1
agpgart                31784  2 drm,intel_agp
pcspkr                  3816  0
rtc                    12216  0
evdev                   9088  0
md                     43856  0
tsdev                   7488  0
dm_mod                 53116  1
capability              5000  0
commoncap               7808  1 capability
psmouse                19336  0
mousedev               11160  1
parport_pc             34372  1
lp                     10792  0
parport                33480  2 parport_pc,lp
ide_cd                 38532  0
cdrom                  36508  1 ide_cd
ext3                  120968  2
jbd                    54168  1 ext3
ide_generic             1664  0
piix                    9988  1
ide_disk               18176  5
ide_core              118988  5 usb_storage,ide_cd,ide_generic,piix,ide_disk
unix                   26164  952
thermal                13576  0
processor              22708  1 thermal
fan                     4612  0
fbcon                  34048  0
font                    8448  1 fbcon
bitblit                 5120  1 fbcon
vesafb                  6948  0
cfbcopyarea             3968  1 vesafb
cfbimgblt               3072  1 vesafb
cfbfillrect             3584  1 vesafb
[/FONT]

---

### Post by PeP on 2005-08-09
says that gtkpod use a deprecated way to talk to your Ipod....
try updating it or switch to amarok

---

### Post by Luke1972 on 2006-12-18
Whilst this thread is very old I'm replying as this is the first hit on a google search on "request beyond eof".  I had the same dmesg error on my external usb hdd and I just unmounted the drive and then removed it and plugged it back in so it remounted itself.  TO unmount all I did was right click ont he desktop icon for it and select the unmount volume option.

---

