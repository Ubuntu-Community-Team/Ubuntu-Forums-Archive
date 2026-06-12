---
title: "[SOLVED] Gutsy doesn't recognize my SATA DVD"
date: 2008-02-21
forum: General Help
---

### Post by teerik on 2008-02-21
My problem is that Gutsy doesn't recognize my SATA DVD drive(s). I used DVD-ROM drive for installation but I never used it to anything else so I don't know if it worked after the installation. Now I purchased a DVD-RW drive and can't get it working (or the DVD-ROM either).

The drive is recognized in BIOS and works perfectly on Windows Vista. When I try to mount it on Ubuntu it says that special device /dev/scd0 doesn't exist. I've made pretty much Googling to find a solution. For some reason Gutsy doesn't seem to know anything about the drive as dmesg and lshw doesn't show anything about it.

The only SATA related stuff I've found is that lspci shows my SATA controller:
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA

But nothing about the drive anywhere.. Can someone help me to solve this problem? Somewhere was some note that Grub has some issues. Could it be the reason and how to fix it if it's all about Grub?

---

### Post by DoctorMO on 2008-02-21
I doubt it's a grub problem. sounds like a hardware problem or a kernel lack of support problem. there is a way to test it.

ls /dev/sd*

should show you all the scsi/sata/ide drive partions and block devices.

In my sig there is a link to Dohickey, install it and it'll look at hal for you and if your cdrom appears in Dohickey then it should work. you just need to figure out where the block node is and mount that.

---

### Post by teerik on 2008-02-21
There are some devices but those are my memory card reader
```
$ ls /dev/sd*
/dev/sda  /dev/sdb  /dev/sdc  /dev/sdd
```

```
$ sudo lshw -C disk
...
  *-disk:0
       description: SCSI Disk
       product: Compact Flash
       vendor: Generic-
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 1.00
       capabilities: removable
     *-disc
          physical id: 0
          logical name: /dev/sda
  *-disk:1
       description: SCSI Disk
       product: SM/xD-Picture
       vendor: Generic-
       physical id: 0.0.1
       bus info: scsi@0:0.0.1
       logical name: /dev/sdb
       version: 1.00
       capabilities: removable
     *-disc
          physical id: 0
          logical name: /dev/sdb
  *-disk:2
       description: SCSI Disk
       product: SD/MMC
       vendor: Generic-
       physical id: 0.0.2
       bus info: scsi@0:0.0.2
       logical name: /dev/sdc
       version: 1.00
       capabilities: removable
     *-disc
          physical id: 0
          logical name: /dev/sdc
  *-disk:3
       description: SCSI Disk
       product: MS/MS-Pro
       vendor: Generic-
       physical id: 0.0.3
       bus info: scsi@0:0.0.3
       logical name: /dev/sdd
       version: 1.00
       capabilities: removable
     *-disc
          physical id: 0
          logical name: /dev/sdd
```

I installed the Dohickey client but it couldn't find the drive either. The drive is Samsung SH-S203D if it helps anyhow.

---

### Post by DoctorMO on 2008-02-21
For some reason the lshw didn't come back with your hard drive, I assume you have one? ide?

Because the drive doesn't appear anywhere in these lists your looking at it being either:

a) unsupported in the kernel at all (unlikely)
b) not compiled or enabled

You may have to search around until you find a sata dvd drive module and modprobe it manually. your other options are to recompile the kernel or even get in touch with kernel developers and pay them to add support for this drive.

It's unusual to find a sata or ide drive that doesn't work in such a drastic fashion. perhaps it has odd or non standard interfaces.

---

### Post by teerik on 2008-02-21
I do have two HDDs. The one dedicated for Ubuntu is IDE drive and lshw lists it. I just cut it off as irrelevant information (see three dots there). I also have SATA drive which is for Vista. It doesn't show up in the lshw list.. It probably should too?

Can you give any hint how to find a module? I'm quite a newbie in these issues and already quite puzzled with this.

---

### Post by DoctorMO on 2008-02-21
OK then now I think it'll be your sata chipset that's not working.

Look in dohickey for your sata chipset under your motherboard and click on it, does it say if it's using a driver? and if so which one? if there isn't a driver then it might be worth adding the module required to get it working.

It may have not loaded up the sata modules since your main linux hard drive isn't sata, although that does seem a bit of stretch. I'm at a loss however as to which module you may need to load, google searches are unfruitful.

you can get a list of sata and ata drivers here:

/lib/modules/`uname -r`/kernel/drivers/ata/

this directory contains all hardware drivers available in the kernel:

/lib/modules/`uname -r`/kernel/drivers

use this command for example foo.so to try and install one and see if it works:

sudo modprobe foo

---

### Post by jespdj on 2008-02-21
I have a similar Samsung SATA DVD writer (SH-S183L). It works without any problems on 64-bit Ubuntu 7.10. I am using it on an Asus motherboard with Intel ICH8 SATA chipset.

You could try plugging in the drive in on a different SATA connector on your motherboard.

---

### Post by DoctorMO on 2008-02-21
jespdj can you post the results from running the following command:

lsmod

Then teerik can you do the same? we can work out what module is and hopefully fix the problem.

---

### Post by teerik on 2008-02-21
> **jespdj said:**
> You could try plugging in the drive in on a different SATA connector on your motherboard.

I could try that if it could help anyhow. But I don't see why it would because the drive is working on Windows. Therefore the connector should be ok?

---

### Post by teerik on 2008-02-21
> **DoctorMO said:**
> Look in dohickey for your sata chipset under your motherboard and click on it, does it say if it's using a driver?

I checked and there isn't any note about driver.

And here's my lsmod list if we could make some comparison with jespdj:

```
Module                  Size  Used by
ipv6                  273892  8 
nls_cp437               6784  0 
cifs                  237428  0 
xt_limit                3584  8 
xt_tcpudp               4224  7 
ipt_LOG                 7552  8 
ipt_MASQUERADE          4608  0 
ipt_TOS                 3200  0 
ipt_REJECT              5760  1 
nf_conntrack_irc        8088  0 
nf_conntrack_ftp       11136  0 
xt_state                3456  6 
af_packet              24840  2 
vmnet                  44596  13 
vmblock                16288  3 
vmmon                 945260  0 
binfmt_misc            12936  1 
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
radeon                125472  2 
drm                    83348  3 radeon
ppdev                  10244  0 
powernow_k8            16960  0 
cpufreq_userspace       5280  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9612  1 
cpufreq_conservative     8072  0 
cpufreq_stats           7232  0 
freq_table              5792  3 powernow_k8,cpufreq_ondemand,cpufreq_stats
container               5504  0 
ac                      6148  0 
video                  18060  0 
button                  8976  0 
dock                   10656  0 
sbs                    19592  0 
battery                11012  0 
lp                     12580  0 
snd_hda_intel         263712  4 
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  3 snd_hda_intel,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
xpad                    9988  0 
parport_pc             37412  1 
parport                37448  3 ppdev,lp,parport_pc
sg                     36764  0 
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  3 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
pcspkr                  4224  0 
serio_raw               8068  0 
k8temp                  6656  0 
sd_mod                 30336  0 
usbhid                 29536  0 
psmouse                39952  0 
snd                    54660  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
hid                    28928  1 usbhid
i2c_piix4               9740  0 
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
i2c_core               26112  1 i2c_piix4
ati_agp                10124  0 
agpgart                35016  2 drm,ati_agp
evdev                  11136  4 
iptable_nat             8708  0 
nf_nat                 20140  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      19724  8 iptable_nat
nf_conntrack           65288  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nfnetlink               6936  3 nf_nat,nf_conntrack_ipv4,nf_conntrack
iptable_mangle          3840  0 
iptable_filter          3968  1 
ip_tables              13924  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               16260  9 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,ipt_TOS,ipt_REJECT,xt_state,iptable_nat,ip_tables
usb_storage            73024  0 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
libusual               18448  1 usb_storage
ide_disk               18560  3 
8139too                27776  0 
atiixp                  7056  0 [permanent]
ide_core              116804  3 usb_storage,ide_disk,atiixp
8139cp                 25088  0 
mii                     6528  2 8139too,8139cp
ohci1394               36528  0 
ieee1394               96312  1 ohci1394
ata_generic             8452  0 
ehci_hcd               36492  0 
ohci_hcd               22916  0 
usbcore               138632  7 xpad,usbhid,usb_storage,libusual,ehci_hcd,ohci_hcd
ahci                   23300  0 
libata                125168  2 ata_generic,ahci
scsi_mod              147084  4 sg,sd_mod,usb_storage,libata
thermal                14344  0 
processor              32072  2 powernow_k8,thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor
```

---

### Post by DoctorMO on 2008-02-21
Indeed there is no sata module there. after many google searches I want you to try this:

sudo modprobe ahci sd_mod sr_mod libata sg cdrom

If it works then you should see more entries in lshw and under /dev/sd*

If you want this to happen each time you switch on the computer add the modules to /etc/modules one per line.

---

### Post by teerik on 2008-02-21
No, it didn't help. Still no signs of SATA drive. After loading I checked with lsmod that *sr_mod* and *cdrom* modules didn't even get loaded. Others exist now on the lsmod list.

---

### Post by DoctorMO on 2008-02-21
the important one is ahci, that seems to be the sata module. check in dohickey again for me.

---

### Post by teerik on 2008-02-21
There's still no driver for SATA chipset even when the ahci module is loaded.

EDIT:
Actually the ahci was all the time loaded. Just checked my post with lsmod listing.

[http://linux-ata.org/driver-status.html#ahci]("http://linux-ata.org/driver-status.html#ahci") states really that it should be the correct module for ATI chipset.

---

### Post by DoctorMO on 2008-02-21
Indeed, well looks like your install has some real problems, it may need personal attention or you may have to reinstall it. what happens when you load a live cd?

---

### Post by teerik on 2008-02-22
I need to consider installing Gutsy over the current Vista installation. Then I would get my SATA HDD in use if the installation succeeds. Only used couple of times Vista and now it's probably time to dump it finally. Then most probably the optical drive would work too as the SATA support has to work for HDD. Probably I should first test with live cd. Have to start downloading it..

---

### Post by teerik on 2008-02-25
Well, it won't even boot to start installation. First it goes fine but when the brown Ubuntu screen with progress bar shows up it drops to the busybox after a while. Wondering how to know what's wrong as I don't get any error message.

EDIT:
Once more I looked on the BIOS settings and just for curiosity I changed SATA mode (from legacy mode to native mode). I didn't even know what it means but I wanted to have a try... and  it solved all problems. My optical SATA drive (/dev/scd0)  is now recognized and automatically mounted on startup by Gutsy and Dohickey also seems to find my another HDD which is a SATA drive and wasn't recognized before. The loaded driver for the SATA chipset is ahci like we previously thought it should be. Hopefully this helps someone with similar problems.

---

### Post by DoctorMO on 2008-02-25
Oh this is good news! I shall remember that a BIOS setting can be the cause for future.

---

