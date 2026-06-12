---
title: "Imsensors?"
date: 2008-03-03
forum: General Help
---

### Post by money2themax on 2008-03-03
i need imsensors to run my HDD Temp sensors

---

### Post by money2themax on 2008-03-03
Meow!

---

### Post by niteshifter on 2008-03-03
I'm guessing that your question is do you need lmsensors to monitor hd temp.

No, hddtemp (in the repositories) is what you need for that. Must be a "modern" hard drive, that is, it has SMART support in the drive.

---

### Post by money2themax on 2008-03-03
> **niteshifter said:**
> I'm guessing that your question is do you need lmsensors to monitor hd temp.

No, hddtemp (in the repositories) is what you need for that. Must be a "modern" hard drive, that is, it has SMART support in the drive.

yes it has SMART but the wigit says it need that

FIXED

now i need fan speed sensors

---

### Post by 3rdalbum on 2008-03-03
sudo apt-get install lm-sensors hddtemp

---

### Post by money2themax on 2008-03-04
ok how about the fan sensors

---

### Post by chewearn on 2008-03-04
lmsensors, among other things, also take care of fan speed readings.

After you install lmsensors, run:
```
sudo sensors-detect
```And choose "yes" to every question.

---

### Post by money2themax on 2008-03-04
i still cant get the volt, fan, or cpu temp sensors working but on the flip side i did get the HDD Temp sensors working

---

### Post by danwood76 on 2008-03-04
What motherboard do you have?

---

### Post by chewearn on 2008-03-04
> **money2themax said:**
> i still cant get the volt, fan, or cpu temp sensors working but on the flip side i did get the HDD Temp sensors working

What exactly do you mean when you said you can't get it working?  Can you post the output of:
```
sudo sensors-detect
```


and 
```
sensors
```

---

### Post by money2themax on 2008-03-04
> **AstalaVista said:**
> What exactly do you mean when you said you can't get it working?  Can you post the output of:
```
sudo sensors-detect
```


```
# sensors-detect revision 4609 (2007-07-14 09:28:39 -0700)

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

We can start with probing for (PCI) I2C or SMBus adapters.
Do you want to probe now? (YES/no): y
Probing for PCI bus adapters...
Use driver `i2c-nforce2' for device 0000:00:0a.1: nVidia Corporation nForce4 SMBus (MCP51)

We will now try to load each adapter module in turn.
Module `i2c-nforce2' already loaded.
If you have undetectable or unsupported adapters, you can have them
scanned by manually loading the modules before running this script.

We are now going to do the I2C/SMBus adapter probings. Some chips may
be double detected; we choose the one with the highest confidence
value in that case.
If you found that the adapter hung after probing a certain address,
you can specify that address to remain unprobed.

Next adapter: SMBus nForce2 adapter at 4c00 (i2c-0)
Do you want to scan it? (YES/no/selectively): y
Client found at address 0x2e
Probing for `Myson MTP008'...                               No
Probing for `National Semiconductor LM78'...                No
Probing for `National Semiconductor LM78-J'...              No
Probing for `National Semiconductor LM79'...                No
Probing for `National Semiconductor LM80'...                No
Probing for `National Semiconductor LM85 or LM96000'...     No
Probing for `Analog Devices ADM1027, ADT7460 or ADT7463'... No
Probing for `SMSC EMC6D100, EMC6D101 or EMC6D102'...        No
Probing for `Analog Devices ADT7462'...                     No
Probing for `Analog Devices ADT7467 or ADT7468'...          No
Probing for `Analog Devices ADT7470'...                     No
Probing for `Analog Devices ADT7473'...                     No
Probing for `Analog Devices ADT7475'...                     No
Probing for `Analog Devices ADT7476'...                     No
Probing for `Andigilog aSC7611'...                          No
Probing for `Andigilog aSC7621'...                          No
Probing for `National Semiconductor LM87'...                No
Probing for `National Semiconductor LM93'...                No
Probing for `Winbond W83781D'...                            No
Probing for `Winbond W83782D'...                            No
Probing for `Winbond W83792D'...                            No
Probing for `Winbond W83793R/G'...                          No
Probing for `Winbond W83791SD'...                           No
Probing for `Winbond W83627HF'...                           No
Probing for `Winbond W83627EHF'...                          No
Probing for `Winbond W83627DHG'...                          No
Probing for `Asus AS99127F (rev.1)'...                      No
Probing for `Asus AS99127F (rev.2)'...                      No
Probing for `Asus ASB100 Bach'...                           No
Probing for `Winbond W83L785TS-S'...                        No
Probing for `Analog Devices ADM9240'...                     No
Probing for `Dallas Semiconductor DS1780'...                No
Probing for `National Semiconductor LM81'...                No
Probing for `Analog Devices ADM1026'...                     No
Probing for `Analog Devices ADM1025'...                     No
Probing for `Analog Devices ADM1024'...                     No
Probing for `Analog Devices ADM1029'...                     No
Probing for `Analog Devices ADM1030'...                     No
Probing for `Analog Devices ADM1031'...                     No
Probing for `Analog Devices ADM1022'...                     No
Probing for `Texas Instruments THMC50'...                   No
Probing for `Analog Devices ADM1028'...                     No
Probing for `ITE IT8712F'...                                No
Probing for `SMSC DME1737'...                               Success!
    (confidence 6, driver `dme1737')
Probing for `Fintek F75373S/SG'...                          No
Probing for `Fintek F75375S/SP'...                          No
Probing for `Fintek F75387SG/RG'...                         No
Probing for `Winbond W83791D'...                            No
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)
Probing for `EDID EEPROM'...                                No
Client found at address 0x51
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)
Probing for `EDID EEPROM'...                                No

Next adapter: SMBus nForce2 adapter at 4c40 (i2c-1)
Do you want to scan it? (YES/no/selectively): y

Next adapter: NVIDIA i2c adapter  (i2c-2)
Do you want to scan it? (YES/no/selectively): y
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Probing for `EDID EEPROM'...                                Yes
    (confidence 8, not a hardware monitoring chip)

Next adapter: NVIDIA i2c adapter  (i2c-3)
Do you want to scan it? (YES/no/selectively): y

Next adapter: NVIDIA i2c adapter  (i2c-4)
Do you want to scan it? (YES/no/selectively): y

Some chips are also accessible through the ISA I/O ports. We have to
write to arbitrary I/O ports to probe them. This is usually safe though.
Yes, you do have ISA I/O ports even if you do not have any ISA slots!
Do you want to scan the ISA I/O ports? (YES/no): y
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM78-J' at 0x290...     No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No
Probing for `Silicon Integrated Systems SIS5595'...         No
Probing for `VIA VT82C686 Integrated Sensors'...            No
Probing for `VIA VT8231 Integrated Sensors'...              No
Probing for `IPMI BMC KCS' at 0xca0...                      No
Probing for `IPMI BMC SMIC' at 0xca8...                     No

Some Super I/O chips may also contain sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): y
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     Yes
Found `SMSC DME1737 Super IO'                               
    (hardware monitoring capabilities accessible via SMBus only)
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       No
Trying family `ITE'...                                      No

Some CPUs or memory controllers may also contain embedded sensors.
Do you want to scan for them? (YES/no): y
AMD K8 thermal sensors...                                   Success!
    (driver `k8temp')
Intel Core family thermal sensor...                         No
Intel AMB FB-DIMM thermal sensor...                         No

Now follows a summary of the probes I have just done.
Just press ENTER to continue: y

Driver `dme1737' (should be inserted):
  Detects correctly:
  * Bus `SMBus nForce2 adapter at 4c00'
    Busdriver `i2c-nforce2', I2C address 0x2e
    Chip `SMSC DME1737' (confidence: 6)

Driver `k8temp' (should be inserted):
  Detects correctly:
  * Chip `AMD K8 thermal sensors' (confidence: 9)

I will now generate the commands needed to load the required modules.
Just press ENTER to continue: y

To make the sensors modules behave correctly, add these lines to
/etc/modules:

#----cut here----
# I2C adapter drivers
i2c-nforce2
# Chip drivers
# Warning: the required module dme1737 is not currently installed
# on your system. For status of 2.6 kernel ports check
# http://www.lm-sensors.org/wiki/Devices. If driver is built
# into the kernel, or unavailable, comment out the following line.
dme1737
k8temp
#----cut here----


Do you want to add these lines to /etc/modules automatically? (yes/NO)y
```

> **AstalaVista said:**
> 
and 
```
sensors
```

```
k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:
             +24°C

```

---

### Post by chewearn on 2008-03-04
Ok, the fan sensors and control are detected to be "SMSC DME1737 Super IO", and the module "dme1737" was added to /etc/modules and loaded at boot.

However, for unknown reason, nothing was reported from this module when you run "sensors" command. Can you verify the module is loaded and running:

```
lsmod | grep dme1737
```

---

### Post by money2themax on 2008-03-05
here

```
money2themax@MX-UBUNTU-000:~$ lsmod | grep dme1737
money2themax@MX-UBUNTU-000:~$ lsmod
Module                  Size  Used by
i2c_dev                 8708  0 
ipv6                  273892  8 
af_packet              24840  2 
binfmt_misc            12936  1 
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ppdev                  10244  0 
powernow_k8            16960  0 
cpufreq_stats           7232  0 
cpufreq_conservative     8072  0 
cpufreq_ondemand        9612  1 
cpufreq_userspace       5280  0 
cpufreq_powersave       2688  0 
freq_table              5792  3 powernow_k8,cpufreq_stats,cpufreq_ondemand
ac                      6148  0 
video                  18060  0 
sbs                    19592  0 
button                  8976  0 
dock                   10656  0 
container               5504  0 
battery                11012  0 
sbp2                   24072  0 
parport_pc             37412  0 
lp                     12580  0 
parport                37448  3 ppdev,parport_pc,lp
snd_hda_intel         263712  2 
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
sg                     36764  0 
nvidia               6221648  34 
psmouse                39952  0 
snd                    54660  13 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sd_mod                 30336  4 
pcspkr                  4224  0 
agpgart                35016  1 nvidia
serio_raw               8068  0 
k8temp                  6656  0 
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
i2c_nforce2             7040  0 
i2c_core               26112  3 i2c_dev,nvidia,i2c_nforce2
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
evdev                  11136  3 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
ide_disk               18560  3 
ide_cd                 32672  0 
cdrom                  37536  1 ide_cd
usb_storage            73024  1 
libusual               18448  1 usb_storage
sata_nv                20612  2 
amd74xx                15260  0 [permanent]
ide_core              116804  4 ide_disk,ide_cd,usb_storage,amd74xx
floppy                 60004  0 
ohci1394               36528  0 
ieee1394               96312  2 sbp2,ohci1394
forcedeth              51592  0 
ata_generic             8452  0 
libata                125168  2 sata_nv,ata_generic
scsi_mod              147084  5 sbp2,sg,sd_mod,usb_storage,libata
ehci_hcd               36492  0 
ohci_hcd               22916  0 
usbcore               138632  5 usb_storage,libusual,ehci_hcd,ohci_hcd
thermal                14344  0 
processor              32072  2 powernow_k8,thermal
fan                     5764  0 
fuse                   47124  5 
apparmor               40728  0 
commoncap               8320  1 apparmor

```

---

### Post by chewearn on 2008-03-05
Ok, looks like the dme1737 module is not running.  Try:
```
sudo modprobe dme1737
```

If you got any error message, post here.  If not, then, try "sensors" again:
```
sensors
```

---

### Post by money2themax on 2008-03-05
ERROR damn

```
money2themax@MX-UBUNTU-000:~$ sudo modprobe dme1737
FATAL: Module dme1737 not found.
```

---

### Post by chewearn on 2008-03-05
I'm not 100% positive here, but my suspicious (after some google search) is that the module dme1737 is only available in kernel later than ver 2.6.22.  In other words, gutsy which has kernel ver 2.6.22 does not have this module.

You can:
1. compile the module yourself (a bit too complicated for me to understand)
[http://lists.lm-sensors.org/pipermail/lm-sensors/2007-December/022166.html](http://lists.lm-sensors.org/pipermail/lm-sensors/2007-December/022166.html)

2. Get/compile a later kernel (also too complicated for me)

3. Wait until April for Hardy 8.04

---

