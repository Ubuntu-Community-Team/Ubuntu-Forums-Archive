---
title: "Kernel panic with Feisty"
date: 2007-09-13
forum: General Help
---

### Post by yhan on 2007-09-13
Hi 

I'm having a really annoying problem with my ubuntu feisty. After 2 or 3 days beeing up the kernel does a panic, as the screen is black, I have no idea why, maybe someone could help. 

My machine is an Athlon base 2600+, installed from scratch with feisty. That machine used to run debian sarge with a 2.4 kernel without any problem, so the problem is software. 

My kernel is 2.6.20-16-generic. 

lspci : 
 > 
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
00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)
00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev c1)
01:07.0 Mass storage controller: Promise Technology, Inc. 20269 (rev 02)
01:08.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
01:0a.0 Multimedia video controller: Internext Compression Inc iTVC15 MPEG-2 Encoder (rev 01)
02:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 440 AGP 8x] (rev c1)


lsmod : 
> 
Module                  Size  Used by
binfmt_misc            12680  1
rfcomm                 40856  0
l2cap                  25856  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
nfs                   240876  0
nfsd                  218992  17
exportfs                6912  1 nfsd
lockd                  64904  3 nfs,nfsd
sunrpc                161340  12 nfs,nfsd,lockd
cx8800                 35212  0
cx88xx                 67364  1 cx8800
bttv                  173684  0
video_buf              26116  3 cx8800,cx88xx,bttv
ir_common              31236  2 cx88xx,bttv
compat_ioctl32          2304  2 cx8800,bttv
btcx_risc               5896  3 cx8800,cx88xx,bttv
lirc_i2c               11268  2
lirc_dev               15988  1 lirc_i2c
ppdev                  10116  0
cpufreq_userspace       5408  0
cpufreq_powersave       2688  0
cpufreq_conservative     8200  0
cpufreq_ondemand        9228  0
cpufreq_stats           7360  0
freq_table              5792  2 cpufreq_ondemand,cpufreq_stats
dev_acpi               12292  0
sony_acpi               6284  0
tc1100_wmi              8068  0
pcc_acpi               13184  0
asus_acpi              17308  0
button                  8720  0
video                  16388  0
dock                   10268  0
backlight               7040  1 asus_acpi
container               5248  0
ac                      6020  0
sbs                    15652  0
i2c_ec                  6016  1 sbs
battery                10756  0
lp                     12452  0
fuse                   46612  1
msp3400                31648  0
saa7115                16400  0
tuner                  61864  0
snd_intel8x0           34332  1
snd_ac97_codec         98464  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0
snd_seq_oss            32896  0
snd_seq_midi            9600  0
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
nvidia               4713780  34
analog                 12832  0
ivtv                  134544  1
snd_mpu401              9256  0
snd_mpu401_uart         9472  1 snd_mpu401
i2c_algo_bit            8712  3 cx88xx,bttv,ivtv
cx2341x                12804  1 ivtv
tveeprom               15888  3 cx88xx,bttv,ivtv
videodev               28160  4 cx8800,cx88xx,bttv,ivtv
v4l2_common            25216  8 cx8800,bttv,msp3400,saa7115,tuner,ivtv,cx2341x,videodev
v4l1_compat            15236  3 cx8800,ivtv,videodev
parport_pc             36388  1
parport                36936  3 ppdev,lp,parport_pc
snd_rawmidi            25472  2 snd_seq_midi,snd_mpu401_uart
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
xpad                    9988  0
gameport               16520  1 analog
serio_raw               7940  0
snd                    54020  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_mpu401,snd_mpu401_uart,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
snd_page_alloc         10888  2 snd_intel8x0,snd_pcm
pcspkr                  4224  0
psmouse                38920  0
shpchp                 34324  0
pci_hotplug            32576  1 shpchp
i2c_nforce2             6784  0
nvidia_agp              9500  1
agpgart                35400  2 nvidia,nvidia_agp
i2c_core               22656  12 cx88xx,bttv,lirc_i2c,i2c_ec,msp3400,saa7115,tuner,nvidia,ivtv,i2c_algo_bit,tveeprom,i2c_nforce2
ipv6                  268960  22
tsdev                   8768  0
evdev                  11008  3
ext3                  133128  6
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
ide_disk               17024  6
ata_generic             9092  0
sata_nv                20868  0
sg                     36252  0
sd_mod                 23428  4
sr_mod                 17060  0
cdrom                  37664  1 sr_mod
amd74xx                15260  0 [permanent]
usbhid                 26592  1
hid                    27392  1 usbhid
usb_storage            72256  1
libusual               17936  1 usb_storage
floppy                 59524  0
generic                 5124  0 [permanent]
pata_pdc2027x          11396  1
libata                125720  3 ata_generic,sata_nv,pata_pdc2027x
scsi_mod              142348  5 sg,sd_mod,sr_mod,usb_storage,libata
forcedeth              46728  0
ehci_hcd               34188  0
ohci_hcd               22532  0
usbcore               134280  8 xpad,usbhid,usb_storage,libusual,ehci_hcd,ohci_hcd
thermal                14856  0
processor              31048  1 thermal
fan                     5636  0
fbcon                  42656  0
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0
capability              5896  0
commoncap               8192  1 capability

/etc/modules : 
 fuse
 lp 
 options ivtv card=85,10 tuner=39,2


The motherboard is an Azus, with a nvidia chipset. The machine is used as a media center with mythtv, with 2 hauppauge cards (250). 
I'm using lirc, I compiled the drivers the package lirc-modules-source                        0.8.1+cvs20070310-0ubuntu2

Everything looks correct in dmesg, I don't have any core, or messages in syslog I could guess of what's goind on ....

Am I the only one to get that problem ? 

Is it possible that the problem might comes from the lirc kernel module ?

Thanks in advance !!

---

### Post by rasdol on 2007-09-13
try to add parameter noapic in the grub boot string in file /boot/grub/menu.lst (or something like this, i don't remember)
it seems to me, that this error is by reason of nvidia chipset

---

### Post by tgalati4 on 2007-09-13
Run memtest86+ for 10 cycles to rule out memory problems.  Also, I've read on the forums with trouble involving serial ports on newer hardware.  The speed differential between the CPU, the data bus, and the serial controller can cause problems.  Using the LIRC routines for a remote control may have highlighted this issue.

You could turn off the serial port in BIOS and not use the remote for a few days and see if that takes care of it.  Of course, it's not helpful to lose a remote control for a MythTV box, but there are other ways to control media PC's:  USB IR remote, Bluetooth keyboards, etc.

---

### Post by yhan on 2007-09-13
I've found this thread : 

[http://ubuntuforums.org/showthread.php?t=488984&page=3](http://ubuntuforums.org/showthread.php?t=488984&page=3)

The first message says to disable the cpu freq freature. The nvidia driver has some troubles to deal with. So I tried that one, We will see. 

Btw the lirc driver I'm using is not for the serial interface, but the infrared controller provider by the hauppauge card.

I'll do anyway the memtest thing, to figure out if it;s a memory problem or not. 

I'll let you know guys if it solved the problem.

---

