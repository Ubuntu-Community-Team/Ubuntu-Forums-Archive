---
title: "Ubuntu 7.10 - system freezes when copying large files"
date: 2007-11-11
forum: General Help
---

### Post by cheddarmakerman on 2007-11-11
I've noticed that when copying large files in Gutsy the system will freeze (mouse and everything) and I'll have to do a hard reboot.  Have others reported this?  Is there a fix/workaround?

---

### Post by ago on 2007-11-11
That has been reported before, but no workaround yet.
What system do you have? What is your HD make and model? On what filesystem was ubuntu installed?

---

### Post by cheddarmakerman on 2007-11-12
Windows XP Professional Service Pack 2
Dell Latitude D620
Samsung SAMSUNG HM060HI	60 GBytes	IDE SATA



Any other info that I can provide that would be help?

---

### Post by ago on 2007-11-12
Can you check the free memory and disk space by keeping up a few monitors while you copy over the files?
Also is that reproducible?

---

### Post by ago on 2007-11-12
Also try to find out what is the required Linux module for your HD. Then add it to

 /etc/initramfs-tools/modules

Then rebuild the initrd with

sudo update-initramfs -u -k $(uname -r)

Then reboot and see if you still have the same issue.

---

### Post by ago on 2007-11-12
You can use lspci -v and hdparm -I to get more info on your HD/controller

---

### Post by cheddarmakerman on 2007-11-13
Hi ago, thanks for the reply.  Yes this problem is reproducible.  I'm trying to install the sun-java6-doc package which requires that you go to sun's website and download the docs zip manually and copy it into the /tmp dir.  When I attempt a copy or move the system freezes almost immediately.

as for the rest.. I'm not a total linux n00b but your instructions were a little over my head.  I was able to run the lspci -v and hdparm -I commands to find out more about my HD controller but I'm not exactly sure what I'm looking for.  I'm assuming that something I see there should point me to the "required Linux module for your HD" but I'm not sure where to look for that either.

I've tried keeping the "system monitor" open while copying a large file and the memory graph stays pretty flat during the whole process.  I'm not exactly sure what you meant by "keeping up a few monitors while you copy over the files"

Wubi is awesome and I'd love to help if someone could just nudge me in the right direction on a few of these things :)

---

### Post by ago on 2007-11-13
Linux "drivers" are called "modules"
All available modules are visible using modprobe -l
Currently active modules are visible via lsmod
And you can "view" your hardware with lsmod -v, hdparm...


With a bit of googling you should be able to figure out what module should be active and if you miss any needed module.

You can then add required modules to 

/etc/initramfs-tools/modules

and update the initrd with update-initramfs -u -k $(uname -r)

Then reboot and retry

That assumes that the crashes are due to a missing (SATA???) module

---

### Post by sal-e on 2007-11-18
Hi Everyone,

I have the same problem. Copying big files or mkfs.ext3 will freeze the system.

I need to resize my home.disk. I create new file called 'newhome.disk' using 'fsutil' in Win XP. Then boot into Ubuntu 7.10 and try to run 'sudo mkfs.ext3 -F /host/ubuntu/disks/newhome.disk'. The command starts ok but shortly after that system freezes. 

I try to use ago's suggestions but so far no success.

1. I run 'sudo hdparm -I /dev/sda'

ATA device, with non-removable media
        Model Number:       ST3320620AS                             
        Serial Number:      9QF3GF1W
        Firmware Revision:  3.AAK   
Standards:
        Supported: 7 6 5 4 
        Likely used: 7
Configuration:
        Logical         max     current
        cylinders       16383   16383
        heads           16      16
        sectors/track   63      63
        --
        CHS current addressable sectors:   16514064
        LBA    user addressable sectors:  268435455
        LBA48  user addressable sectors:  625142448
        device size with M = 1024*1024:      305245 MBytes
        device size with M = 1000*1000:      320072 MBytes (320 GB)
Capabilities:
        LBA, IORDY(can be disabled)
        Queue depth: 32
        Standby timer values: spec'd by Standard, no device specific minimum
        R/W multiple sector transfer: Max = 16  Current = 16
        Recommended acoustic management value: 254, current value: 0
        DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
             Cycle time: min=120ns recommended=120ns
        PIO: pio0 pio1 pio2 pio3 pio4 
             Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
        Enabled Supported:
           *    SMART feature set
                Security Mode feature set
           *    Power Management feature set
           *    Write cache
           *    Look-ahead
           *    Host Protected Area feature set
           *    WRITE_BUFFER command
           *    READ_BUFFER command
           *    DOWNLOAD_MICROCODE
                SET_MAX security extension
           *    48-bit Address feature set
           *    Device Configuration Overlay feature set
           *    Mandatory FLUSH_CACHE
           *    FLUSH_CACHE_EXT
           *    SMART error logging
           *    SMART self-test
           *    General Purpose Logging feature set
           *    SATA-I signaling speed (1.5Gb/s)
           *    SATA-II signaling speed (3.0Gb/s)
           *    Native Command Queueing (NCQ)
           *    Phy event counters
                Device-initiated interface power management
           *    Software settings preservation
Security: 
        Master password revision code = 65534
                supported
        not     enabled
        not     locked
                frozen
        not     expired: security count
        not     supported: enhanced erase
Checksum: correct

2. I run 'sudo lspci -v'
...
00.1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: ASUSTeK Computer Inc. Unknown device 2601
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 23
        I/O ports at e400 [size=8]
        I/O ports at e080 [size=4]
        I/O ports at e000 [size=8]
        I/O ports at dc00 [size=4]
        I/O ports at d880 [size=16]
        Memory at ffafb800 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [70] Power Management version 2

02:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02) (prog-if 01 [AHCI 1.0])
        Subsystem: ASUSTeK Computer Inc. Unknown device 81e4
        Flags: bus master, fast devsel, latency 0, IRQ 18
        Memory at ff7fe000 (32-bit, non-prefetchable) [size=8K]
        Expansion ROM at ff7e0000 [disabled] [size=64K]
        Capabilities: [68] Power Management version 2
        Capabilities: [50] Express Legacy Endpoint IRQ 1
...

After reading on google I try to add 'sd_mod' and 'ata_piix' into '/etc/initramfs-tools/modules' but 'sudo update-initramfs -u -k $(uname -r)' failed:
WARNING: /boot is ro mounted.
update-initramfs: Not updating /boot/initrd.img-2.6.22-14-generic

After some break, I think this is not going to help because 'lsmod' clearly show that 'sd_mod' and 'ata_piix' are active and used.

Module                  Size  Used by
ipv6                  273892  10 
af_packet              24840  2 
fglrx                 656352  15 
agpgart                35016  1 fglrx
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ppdev                  10244  0 
acpi_cpufreq           10568  0 
cpufreq_powersave       2688  0 
cpufreq_conservative     8072  0 
cpufreq_userspace       5280  0 
cpufreq_ondemand        9612  2 
cpufreq_stats           7232  0 
freq_table              5792  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
ac                      6148  0 
sbs                    19592  0 
container               5504  0 
dock                   10656  0 
button                  8976  0 
video                  18060  0 
battery                11012  0 
sbp2                   24072  0 
parport_pc             37412  0 
lp                     12580  0 
parport                37448  3 ppdev,parport_pc,lp
joydev                 11328  0 
arc4                    2944  2 
ecb                     4608  2 
blkcipher               7556  1 ecb
rc80211_simple          6912  1 
xpad                    9988  0 
wacom                  17664  0 
snd_hda_intel         263712  1 
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
rtl8187                35328  0 
mac80211              171016  2 rc80211_simple,rtl8187
cfg80211                7304  1 mac80211
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
eeprom_93cx6            3200  1 rtl8187
usbhid                 29536  0 
hid                    28928  1 usbhid
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
sky2                   46852  0 
pcspkr                  4224  0 
psmouse                39952  0 
serio_raw               8068  0 
snd                    54660  11 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
iTCO_wdt               11940  0 
iTCO_vendor_support     4868  1 iTCO_wdt
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
evdev                  11136  4 
ext3                  133896  3 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
loop                   19076  6 
sg                     36764  0 
sr_mod                 17828  0 
sd_mod                 30336  2 
cdrom                  37536  1 sr_mod
pata_jmicron            7552  0 
ahci                   23300  0 
floppy                 60004  0 
ehci_hcd               36492  0 
ohci1394               36528  0 
ieee1394               96312  2 sbp2,ohci1394
uhci_hcd               26640  0 
ata_piix               17540  1 
ata_generic             8452  0 
libata                125168  4 pata_jmicron,ahci,ata_piix,ata_generic
scsi_mod              147084  5 sbp2,sg,sr_mod,sd_mod,libata
usbcore               138632  7 xpad,wacom,rtl8187,usbhid,ehci_hcd,uhci_hcd
thermal                14344  0 
processor              32072  2 acpi_cpufreq,thermal
fan                     5764  0 
fuse                   47124  3 
apparmor               40728  0 
commoncap               8320  1 apparmor

Exact same configuration worked without any problems with Wubi 7.04

Is any one have any idea what is wrong here?

Thank you,
SAL-e

---

### Post by ago on 2007-11-19
In the worst case it is due to a kernel issues, which requires a new kernel with the patch (2.6.24).

In the best case it is a wrong SATA driver which should be fixable with modprobe and/or initramfs-tools/modules

---

### Post by maravena on 2007-12-03
Hi!!!

I think the problem is NOT SATA disk, because i have the same problem with my PC (IDE PATA)

bye!!

---

