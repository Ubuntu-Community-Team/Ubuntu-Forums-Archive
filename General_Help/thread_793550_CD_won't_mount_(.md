---
title: "CD won't mount :("
date: 2008-05-13
forum: General Help
---

### Post by doorknob60 on 2008-05-13
Well, I'm kinda cheating, because this is on my Debian Etch system, but whatever :P Anyways, I can't get any CDs to mount. I know my drive and CD is good because they work in Windows and I used them to install Debian yesterday. Also, yesterday it let me use the CD as a repository to install the dependencies to build my wifi driver (no ethernet :P), so something must have happened since then (possibly that kernel upgrade?). When I try to mount it gives this error:
> mount: No medium found

After that, this shows up in dmesg:
> hdc: packet command error: status=0x51 { DriveReady SeekComplete Error }
hdc: packet command error: error=0x50 { LastFailedSense=0x05 }
ide: failed opcode was: unknown

Here's my fstab:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /windows        vfat    defaults,user
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/cdrom      /media/cdrom0   udf,iso9660 user        0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


/dev/hdc is my cd drive and /dev/cdrom is linked to it, and *any* mount command I try gives the same error. Remeber that I think I didn't have this problem earlier (likely before the update). Would upgrading to Debian Lenny (using etch right now) or reinstalling some packages (if so, which ones?) help? Thanks in advance!

---

### Post by ironwolfe on 2008-05-13
You are missing the line in your fstab:

```
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto,exec 0 0

```

I think you can even comment the other cdrom line out with a #.

that should do it.

EDIT 1:  I would create the link between cdrom and cdrom0 outside the fstab.

```
sudo ln -s /media/cdrom0 /media/cdrom
```

---

### Post by doorknob60 on 2008-05-13
Didn't change a thing :( Gives the same not-so-helpful error -.-

---

### Post by ironwolfe on 2008-05-13
hmmmm.

found this thread - seems like it is a hotplug driver issue:

[http://ubuntuforums.org/archive/index.php/t-2264.html](http://ubuntuforums.org/archive/index.php/t-2264.html)

try disabling DMA on the drive and see if that helps:

```
echo 'using_dma:0' | sudo tee /proc/ide/hdc/settings
```

also post results from 

```
lsmod
```

---

### Post by ironwolfe on 2008-05-13
I don't know what to do with this:

> Toshiba laptops have special extensions to their power management (ACPI) drivers, in order for them to work properly under Linux and not fry themselves.

The Hotplug detection routine "thought" that your system needed these Toshiba drivers. When it loaded the drivers, the driver couldn't find Toshiba hardware, and thus refused to stay active. It's perfectly normal.

Same explanation for the ****hp drivers. Those are hotplug drivers... If you can't rip PCI cards out of your box while it's turned on, you don't have PCI hotpug :grin:


In short, these errors have no connection whatsoever to a broken drive.

---

### Post by doorknob60 on 2008-05-13
Lsmod output:
> austin@austin-laptop:~$ lsmod
Module                  Size  Used by
wlan_wep                6528  1
wlan_scan_sta          11520  1
ath_rate_sample        11264  1
ath_pci                82592  0
wlan                  175984  5 wlan_wep,wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               191568  3 ath_rate_sample,ath_pci
ipv6                  213984  10
ppdev                   8708  0
lp                     10948  0
button                  6800  0
ac                      5252  0
battery                 9732  0
isofs                  31928  0
udf                    72324  0
nls_iso8859_1           4352  1
nls_cp437               6016  1
vfat                   11648  1
fat                    45980  1 vfat
dm_snapshot            15644  0
dm_mirror              18000  0
dm_mod                 48952  2 dm_snapshot,dm_mirror
loop                   14216  0
snd_es1938             19492  1
gameport               13832  2 snd_es1938
snd_pcm_oss            38048  0
snd_mixer_oss          15232  1 snd_pcm_oss
snd_pcm                65928  2 snd_es1938,snd_pcm_oss
snd_page_alloc         10248  1 snd_pcm
snd_opl3_lib            9600  1 snd_es1938
snd_hwdep               8836  1 snd_opl3_lib
snd_mpu401_uart         7552  1 snd_es1938
pcmcia                 33852  0
firmware_class          9472  1 pcmcia
snd_seq_dummy           3972  0
snd_seq_oss            27648  0
floppy                 52004  0
snd_seq_midi            8352  0
snd_seq_midi_event      6784  2 snd_seq_oss,snd_seq_midi
snd_seq                42192  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
parport_pc             31524  1
snd_timer              19972  3 snd_pcm,snd_opl3_lib,snd_seq
parport                32200  3 ppdev,lp,parport_pc
snd_rawmidi            22048  2 snd_mpu401_uart,snd_seq_midi
snd_seq_device          7820  6 snd_opl3_lib,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
rtc                    11572  0
i2c_ali1535             6660  0
i2c_ali15x3             7428  0
i2c_core               19472  2 i2c_ali1535,i2c_ali15x3
serio_raw               6532  0
snd                    45412  14 snd_es1938,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_opl3_lib,snd_hwdep,snd_mpu401_uart,snd_seq_oss,snd_seq,snd_timer,snd_rawmidi,snd_seq_device
psmouse                34568  0
ali_agp                 6784  1
agpgart                29360  1 ali_agp
pcspkr                  2816  0
shpchp                 32796  0
pci_hotplug            28088  1 shpchp
soundcore               8928  1 snd
yenta_socket           24588  2
rsrc_nonstatic         11904  1 yenta_socket
pcmcia_core            36240  3 pcmcia,yenta_socket,rsrc_nonstatic
joydev                  9152  0
tsdev                   7616  0
evdev                   9088  1
ext3                  116488  1
jbd                    47272  1 ext3
usbhid                 35808  0
ide_cd                 35616  0
cdrom                  32416  1 ide_cd
ide_disk               14848  4
generic                 4996  0 [permanent]
ohci_hcd               17540  0
usbcore               109444  3 usbhid,ohci_hcd
alim15x3               11148  0 [permanent]
ide_core              107760  4 ide_cd,ide_disk,generic,alim15x3
thermal                13576  0
processor              23724  1 thermal
fan                     4868  0
austin@austin-laptop:~$

Also, disabling the DMA didn't seem to help, unless I need to restart first, which I will as soon as I'm done with sudo apt-get upgrade (installing an updated kernel, wish me luck). Also, what doesn't make sense is that it works in 2.4 kernels (DSL) and other 2.6 kernels (Fluxbuntu), and I think it worked for a while after the fresh Debian install...

---

### Post by ironwolfe on 2008-05-14
your modules look ok to me - I am not sure why it isn't working.  Unless the modules in the newer kernel have fixed a bug...

just a thought - turn off the hotplug

sudo modprobe -r pci_hotplug

you can always add it back

sudo modprobe pci_hotplug 

good luck

---

### Post by doorknob60 on 2008-05-14
I'd try that, but apperantly my CD drive isn't working at all :P Tried using a live cd again and it didn't work, and windows doesn't like it any more either. O'm sure it's a loose cable or something, but I don't have the appropriate tools to open my laptop....meh :(

Don't get mad at me for not checking this earlier, but a CD drive being detected properly by the BIOS and the OS but not being able to be mounted immediately after a kernel update is pretty suspicious :P

---

