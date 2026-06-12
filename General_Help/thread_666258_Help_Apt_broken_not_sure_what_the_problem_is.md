---
title: "Help Apt broken not sure what the problem is"
date: 2008-01-13
forum: General Help
---

### Post by gezzabob on 2008-01-13
Hi all,

Was installing various themes from synaptic and it failed with the error please run dpkg-reconfigure to fix so ran that but got errors.

Here is what happens when I run dpkg-reconfigure ...

geoffl@geoffl-desktop:~$ sudo dpkg-reconfigure -a
 * Disabling power management...                                         [ OK ] 
 * Checking battery state...                                             [ OK ] 
 * Stopping ACPI services...                                             [ OK ] 
 * Loading ACPI modules...                                               [ OK ] 
 * Starting ACPI services...                                             [ OK ] 
 * Stopping anac(h)ronistic cron anacron                                 [ OK ] 
 * Starting anac(h)ronistic cron anacron                                 [ OK ] 
Caching application data...
Skipped k3dsurf.desktop: does not include a menu name
Generating mime/codec maps...
Caching application data...
Skipped k3dsurf.desktop: does not include a menu name
Generating mime/codec maps...
update-initramfs: Generating /boot/initrd.img-2.6.23.12
Cannot find /lib/modules/2.6.23.12
update-initramfs: failed for /boot/initrd.img-2.6.23.12
geoffl@geoffl-desktop:~$ 

Any ideas please of what the problem is and where I start to fix this?

---

### Post by gezzabob on 2008-01-13
Well just ran a sudo apt-get clean and then sudo apt-get update and the error message seems to have gone now?

So I guess this has been solved....

---

### Post by gezzabob on 2008-01-13
A little off topic but ...

How do I change the thead title that displays on the main page its a little deceiving?  I have edited the post and changed the title thinking it will change it but only when you click on the post do you see the new title?

---

### Post by gezzabob on 2008-01-13
Well I thought apt-get clean fix the problem but the error update-initramfs: failed for /boot/initrd.img-2.6.23.12

is back and asking me to run dpkg-reconfigure -a but thats what is giving me the error messages.

Any ideas please?

---

### Post by gezzabob on 2008-01-13
My apt source list..

geoffl@geoffl-desktop:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

#AUTOMATIX REPOS START

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) gutsy main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-backports main restricted universe multiverse
#AUTOMATIX REPOS END
geoffl@geoffl-desktop:~$

---

### Post by gezzabob on 2008-01-13
I am running Gusty and some other details that maybe helpful.

geoffl@geoffl-desktop:~$ uname -a
Linux geoffl-desktop 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 i686 GNU/Linux
geoffl@geoffl-desktop:~$ lspci
00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (rev c1)
00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev c1)
00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev c1)
00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev c1)
00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev c1)
00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev c1)
00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a4)
00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
00:05.0 Multimedia audio controller: nVidia Corporation nForce Audio Processing Unit (rev a2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)
00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
00:0d.0 FireWire (IEEE 1394): nVidia Corporation nForce2 FireWire (IEEE 1394) Controller (rev a3)
00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev c1)
01:09.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
01:09.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
01:0b.0 Ethernet controller: Intel Corporation 82540EM Gigabit Ethernet Controller (rev 02)
01:0c.0 RAID bus controller: Integrated Technology Express, Inc. IT/ITE8212 Dual channel ATA RAID controller (rev 10)
01:0d.0 Mass storage controller: Silicon Image, Inc. SiI 3112 [SATALink/SATARaid] Serial ATA Controller (rev 02)
03:00.0 VGA compatible controller: nVidia Corporation NV40 [GeForce 6800 GT] (rev a1)
geoffl@geoffl-desktop:~$

---

### Post by gezzabob on 2008-01-13
geoffl@geoffl-desktop:~$ getopt -V
getopt (enhanced) 1.1.4
geoffl@geoffl-desktop:~$

---

### Post by gezzabob on 2008-01-13
geoffl@geoffl-desktop:~$ lsmod
Module                  Size  Used by
nls_iso8859_1           5120  0 
vfat                   14080  0 
fat                    54300  1 vfat
nls_cp437               6784  0 
isofs                  36412  0 
udf                    87204  0 
snd_rtctimer            4384  1 
binfmt_misc            12936  1 
ipv6                  273892  14 
af_packet              24840  2 
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
ppdev                  10244  0 
cpufreq_userspace       5280  0 
cpufreq_ondemand        9612  0 
cpufreq_conservative     8072  0 
cpufreq_powersave       2688  0 
cpufreq_stats           7232  0 
freq_table              5792  2 cpufreq_ondemand,cpufreq_stats
button                  8976  0 
ac                      6148  0 
video                  18060  0 
container               5504  0 
sbs                    19592  0 
dock                   10656  0 
battery                11012  0 
sbp2                   24072  0 
lp                     12580  0 
snd_mpu401              9640  0 
snd_mpu401_uart         9600  1 snd_mpu401
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
bt878                  11832  0 
snd_intel8x0           34972  3 
snd_ac97_codec        100644  1 snd_intel8x0
nvidia               6221648  34 
snd_seq_midi            9600  0 
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq                53232  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  4 snd_rtctimer,snd_pcm,snd_seq
snd_rawmidi            25728  2 snd_mpu401_uart,snd_seq_midi
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
bttv                  177012  1 bt878
video_buf              26244  1 bttv
ir_common              35460  1 bttv
compat_ioctl32          2304  1 bttv
i2c_algo_bit            7428  1 bttv
btcx_risc               5896  1 bttv
tveeprom               16784  1 bttv
videodev               29312  1 bttv
v4l2_common            18432  2 bttv,videodev
v4l1_compat            15364  2 bttv,videodev
serio_raw               8068  0 
pcspkr                  4224  0 
parport_pc             37412  1 
parport                37448  3 ppdev,lp,parport_pc
analog                 13344  0 
gameport               16776  1 analog
snd                    54660  17 snd_mpu401,snd_mpu401_uart,snd_seq_oss,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq,snd_timer,snd_rawmidi,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
psmouse                39952  0 
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
hci_usb                18332  2 
bluetooth              57060  7 rfcomm,l2cap,hci_usb
i2c_nforce2             7040  0 
i2c_core               26112  5 nvidia,bttv,i2c_algo_bit,tveeprom,i2c_nforce2
nvidia_agp              9756  1 
agpgart                35016  2 nvidia,nvidia_agp
evdev                  11136  3 
ext3                  133896  4 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
ide_cd                 32672  0 
cdrom                  37536  1 ide_cd
ide_disk               18560  7 
usb_storage            73024  0 
libusual               18448  1 usb_storage
usbhid                 29536  0 
hid                    28928  1 usbhid
sg                     36764  0 
sd_mod                 30336  7 
amd74xx                15260  0 [permanent]
ide_core              116804  4 ide_cd,ide_disk,usb_storage,amd74xx
floppy                 60004  0 
sata_sil               12168  1 
ata_generic             8452  0 
pata_it821x            12292  3 
libata                125168  3 sata_sil,ata_generic,pata_it821x
scsi_mod              147084  5 sbp2,usb_storage,sg,sd_mod,libata
e1000                 126272  0 
ohci1394               36528  0 
ieee1394               96312  2 sbp2,ohci1394
forcedeth              51592  0 
ehci_hcd               36492  0 
ohci_hcd               22916  0 
usbcore               138632  7 hci_usb,usb_storage,libusual,usbhid,ehci_hcd,ohci_hcd
thermal                14344  0 
processor              32072  1 thermal
fan                     5764  0 
fuse                   47124  9 
apparmor               40728  0 
commoncap               8320  1 apparmor
geoffl@geoffl-desktop:~$

---

### Post by gezzabob on 2008-01-13
I think I have managed to get passed that error of update-initramfs: failed for /boot/initrd.img-2.6.23.12
..
I created a empty directory - /lib/modules/2.6.23.12

---

