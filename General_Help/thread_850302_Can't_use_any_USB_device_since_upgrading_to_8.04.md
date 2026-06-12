---
title: "Can't use any USB device since upgrading to 8.04"
date: 2008-07-05
forum: General Help
---

### Post by tmastran on 2008-07-05
I'm having a problem using any USB device since upgrading to Ubuntu 8.04 from the previous version.

The output below is what I get when I plug in a Canon USB camera, or pretty much any USB device. It doesn't
get any farther.

What should I do next? Thanks!

# tail -f /var/log/messages
Jul  5 11:14:44 delphi kernel: [1339075.773691] usb 4-2: new full speed USB device using uhci_hcd and address 5
Jul  5 11:14:44 delphi kernel: [1339075.937605] usb 4-2: configuration #1 chosen from 1 choice

# cat /etc/issue
Ubuntu 8.04.1 \n \l

# uname -a
Linux pc.org 2.6.24-19-generic #1 SMP Wed Jun 18 14:43:41 UTC 2008 i686 GNU/Linux

# lsusb
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

lsmod
Module                  Size  Used by
ehci_hcd               37900  0
uhci_hcd               27024  0
usbcore               146028  3 ehci_hcd,uhci_hcd
ip6table_filter         3584  0
ip6_tables             15844  1 ip6table_filter
snd_rtctimer            4640  0
isofs                  36388  1
loop                   18948  5
binfmt_misc            12808  1
rfcomm                 41744  2
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0
speedstep_lib           6532  0
cpufreq_userspace       5284  0
cpufreq_stats           7104  0
cpufreq_powersave       2688  0
cpufreq_ondemand        9740  0
freq_table              5536  2 cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     8712  0
video                  19856  0
output                  4736  1 video
sbs                    15112  0
sbshc                   7680  1 sbs
dock                   11280  0
container               5632  0
battery                14212  0
iptable_filter          3840  0
ip_tables              14820  1 iptable_filter
x_tables               16132  2 ip6_tables,ip_tables
nls_iso8859_1           4992  2
nls_cp437               6656  3
vfat                   14464  2
fat                    54556  1 vfat
aes_i586               33536  0
dm_crypt               15364  0
dm_mod                 62660  1 dm_crypt
ac                      6916  0
w83627hf               23444  0
hwmon_vid               4352  1 w83627hf
lp                     12324  0
ipv6                  267780  16
snd_intel8x0           35356  0
snd_ac97_codec        101028  1 snd_intel8x0
ac97_bus                3072  1 snd_ac97_codec
nvidia               7106340  24
snd_pcm_oss            42144  0
snd_pcm                78596  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_mixer_oss          17920  1 snd_pcm_oss
serio_raw               7940  0
i2c_core               24832  1 nvidia
snd_seq_dummy           4868  0
snd_seq_oss            35584  0
snd_seq_midi            9376  0
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
parport_pc             36260  1
button                  9232  0
parport                37832  3 ppdev,lp,parport_pc
evdev                  13056  3
intel_agp              25492  1
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  3 snd_rtctimer,snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
agpgart                34760  2 nvidia,intel_agp
snd                    56996  12 snd_rtctimer,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
shpchp                 34452  0
pci_hotplug            30880  1 shpchp
soundcore               8800  1 snd
iTCO_wdt               13092  0
iTCO_vendor_support     4868  1 iTCO_wdt
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
psmouse                40336  0
pcspkr                  4224  0
ext3                  136712  4
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sr_mod                 17956  2
cdrom                  37408  1 sr_mod
sd_mod                 30720  9
sg                     36880  0
sbp2                   24072  0
ata_piix               19588  9
pata_acpi               8320  0
ata_generic             8324  0
floppy                 59588  0
ohci1394               33584  1
aic7xxx               178264  0
scsi_transport_spi     25472  1 aic7xxx
ieee1394               93752  2 sbp2,ohci1394
libata                159344  3 ata_piix,pata_acpi,ata_generic
scsi_mod              151436  7 sr_mod,sd_mod,sg,sbp2,aic7xxx,scsi_transport_spi,libata
e100                   37388  0
mii                     6400  1 e100
thermal                16796  0
processor              36872  1 thermal
fan                     5636  0
fbcon                  42912  0
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  4

---

### Post by pytheas22 on 2008-07-05
Does the system lock up completely when you plug in the device?  Have you tried at least a few other devices--and not just cameras but also USB storage devices, printers, wireless cards, et cetera?

If it doesn't lock up completely, please post the output of:
```

dmesg
```

a few seconds after you plug in the device.

Also, it might help to do this before plugging in the camera:
```

sudo rmmod uhci_hcd
sudo modprobe ehci_hcd
```

This will disable USB 2.0 protocol and revert to 1.1.  It will be slower but might prevent the freeze, which would tell us where the problem lies.

---

### Post by spiderbatdad on 2008-07-05
you might try "usbmount" in synaptic package manager.

---

### Post by mempman on 2008-07-05
lsusb is very restricting unless you use it in verbose mode:

i.e. lsusb -vv

Typically for usb devices are accessible via /dev/sd[a-z]...try mounting like the first 5 or so.

---

### Post by tmastran on 2008-07-05
> **pytheas22 said:**
> Does the system lock up completely when you plug in the device?  Have you tried at least a few other devices--and not just cameras but also USB storage devices, printers, wireless cards, et cetera?

If it doesn't lock up completely, please post the output of:
```

dmesg
```

a few seconds after you plug in the device.

Also, it might help to do this before plugging in the camera:
```

sudo rmmod uhci_hcd
sudo modprobe ehci_hcd
```

This will disable USB 2.0 protocol and revert to 1.1.  It will be slower but might prevent the freeze, which would tell us where the problem lies.

The system does not lock up. dmesg output is the same as the message log:

[1370137.449905] usb 1-8: new high speed USB device using ehci_hcd and address 6
[1370137.593533] usb 1-8: configuration #1 chosen from 1 choice

I've tried the rmmod/modprobe and that doesn'r work either.

---

### Post by tmastran on 2008-07-05
> **mempman said:**
> lsusb is very restricting unless you use it in verbose mode:

i.e. lsusb -vv

Typically for usb devices are accessible via /dev/sd[a-z]...try mounting like the first 5 or so.

If I remember, when it used to work they were mounted as /dev/sdc[n]. I don't have any mountable /dev/sd[a-z]. The one's I do are hard disk partitions.

Here's the long lsusb:

# lsusb -vv

Bus 005 Device 001: ID 0000:0000
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x0000
  idProduct          0x0000
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.24-19-generic uhci_hcd
  iProduct                2 UHCI Host Controller
  iSerial                 1 0000:00:1d.3
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             2
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
  bPwrOn2PwrGood        1 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

Bus 004 Device 001: ID 0000:0000
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x0000
  idProduct          0x0000
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.24-19-generic uhci_hcd
  iProduct                2 UHCI Host Controller
  iSerial                 1 0000:00:1d.2
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             2
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
  bPwrOn2PwrGood        1 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

Bus 003 Device 001: ID 0000:0000
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x0000
  idProduct          0x0000
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.24-19-generic uhci_hcd
  iProduct                2 UHCI Host Controller
  iSerial                 1 0000:00:1d.1
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             2
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
  bPwrOn2PwrGood        1 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

Bus 002 Device 001: ID 0000:0000
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x0000
  idProduct          0x0000
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.24-19-generic uhci_hcd
  iProduct                2 UHCI Host Controller
  iSerial                 1 0000:00:1d.0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             2
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
  bPwrOn2PwrGood        1 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

Bus 001 Device 001: ID 0000:0000
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         1 Single TT
  bMaxPacketSize0        64
  idVendor           0x0000
  idProduct          0x0000
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.24-19-generic ehci_hcd
  iProduct                2 EHCI Host Controller
  iSerial                 1 0000:00:1d.7
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              12
Hub Descriptor:
  bLength              11
  bDescriptorType      41
  nNbrPorts             8
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
    TT think time 8 FS bits
  bPwrOn2PwrGood       10 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00 0x00
  PortPwrCtrlMask    0xff 0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
   Port 3: 0000.0100 power
   Port 4: 0000.0100 power
   Port 5: 0000.0100 power
   Port 6: 0000.0100 power
   Port 7: 0000.0100 power
   Port 8: 0000.0503 highspeed power enable connect
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

Thanks for the help

---

### Post by tmastran on 2008-07-05
> **spiderbatdad said:**
> you might try "usbmount" in synaptic package manager.

Thanks, but this did not work.

---

### Post by tmastran on 2008-07-05
I decided to try a usb CF card reader instead of the camera and got nothing, then remembered needing to load this module for it:

# modprobe usb_storage

Now I get the is system message output:

Jul  5 20:17:36 delphi kernel: [1371585.897357] usb 1-7: USB disconnect, address 16
Jul  5 20:17:39 delphi kernel: [1371588.722974] usb 1-7: new high speed USB device using ehci_hcd and address 17
Jul  5 20:17:39 delphi kernel: [1371588.865494] usb 1-7: configuration #1 chosen from 1 choice
Jul  5 20:17:39 delphi kernel: [1371588.866039] scsi12 : SCSI emulation for USB Mass Storage devices
Jul  5 20:17:44 delphi kernel: [1371593.884310] scsi 12:0:0:0: Direct-Access     Generic  STORAGE DEVICE   1.00 PQ: 0 ANSI: 0
Jul  5 20:17:44 delphi kernel: [1371593.886143] sd 12:0:0:0: [sdc] 503808 512-byte hardware sectors (258 MB)
Jul  5 20:17:44 delphi kernel: [1371593.887146] sd 12:0:0:0: [sdc] Write Protect is off
Jul  5 20:17:44 delphi kernel: [1371593.889761] sd 12:0:0:0: [sdc] 503808 512-byte hardware sectors (258 MB)
Jul  5 20:17:44 delphi kernel: [1371593.891140] sd 12:0:0:0: [sdc] Write Protect is off
Jul  5 20:17:44 delphi kernel: [1371593.891159]  sdc: sdc1
Jul  5 20:17:44 delphi kernel: [1371593.893516] sd 12:0:0:0: [sdc] Attached SCSI removable disk
Jul  5 20:17:44 delphi kernel: [1371593.893590] sd 12:0:0:0: Attached scsi generic sg6 type 0

It looks like I should be able to mount /dev/sdc1 now, but that device does not exist. Is that my problem? sdc1 is not being created? I don't have a /dev/sg6 either. Oddly there is an sg1 through 5.

Still stumped.

---

### Post by pytheas22 on 2008-07-05
I got ehci and uhci mixed up...ehci is high-speed.  Does this help:
```

sudo rmmod ehci_usb
sudo modprobe uhci_usb
```

> It looks like I should be able to mount /dev/sdc1 now, but that device does not exist. Is that my problem? sdc1 is not being created? I don't have a /dev/sg6 either. Oddly there is an sg1 through 5.

Do you know what sg1-5 are?  Did they exist before you plugged that device in?  Also are you positive that absolutely no entry is being created when you plug this device in?  You could use diff to be sure, e.g.:
```

ls /dev > before
```

then plug it in, then:
```

ls /dev > after
diff before after
```

would tell you about any differences in /dev between when the device is plugged in and when it's not.  This could be good to know.  Maybe it's creating it under the wrong name.

---

### Post by tmastran on 2008-07-06
> **pytheas22 said:**
> I got ehci and uhci mixed up...ehci is high-speed.  Does this help:
```

sudo rmmod ehci_usb
sudo modprobe uhci_usb
```



Do you know what sg1-5 are?  Did they exist before you plugged that device in?  Also are you positive that absolutely no entry is being created when you plug this device in?  You could use diff to be sure, e.g.:
```

ls /dev > before
```

then plug it in, then:
```

ls /dev > after
diff before after
```

would tell you about any differences in /dev between when the device is plugged in and when it's not.  This could be good to know.  Maybe it's creating it under the wrong name.

The module load/unload did not help. sg1-5 did exist before plugging in the USB card reader. Diff before/after shows no change. ls -l on them shows who owns them, sg0 and sg5 are my two film scanners. One is a scsi device, the other is a firewire device. I went with firewire on the one scanner (that also supports USB) because I could not get it to work similar to my current problem.

brw-rw----+ 1 root cdrom   11,   0 2008-06-19 17:34 /dev/scd0
brw-rw----+ 1 root cdrom   11,   1 2008-06-19 17:34 /dev/scd1
brw-rw----  1 root disk     8,   0 2008-06-19 17:34 /dev/sda
brw-rw----  1 root disk     8,   1 2008-06-19 17:34 /dev/sda1
brw-rw----  1 root disk     8,   2 2008-06-19 17:34 /dev/sda2
brw-rw----  1 root disk     8,   3 2008-06-19 17:34 /dev/sda3
brw-rw----  1 root disk     8,   4 2008-06-19 17:34 /dev/sda4
brw-rw----  1 root disk     8,  16 2008-06-19 17:34 /dev/sdb
brw-rw----  1 root disk     8,  17 2008-06-19 17:34 /dev/sdb1
brw-rw----  1 root disk     8,  18 2008-06-19 17:34 /dev/sdb2
brw-rw----  1 root disk     8,  21 2008-06-19 22:34 /dev/sdb5
brw-rw----  1 root disk     8,  22 2008-06-19 17:34 /dev/sdb6
brw-rw----  1 root disk     8,  23 2008-06-19 22:34 /dev/sdb7
crw-rw----+ 1 root audio   14,   1 2008-06-19 22:33 /dev/sequencer
crw-rw----+ 1 root audio   14,   8 2008-06-19 22:33 /dev/sequencer2
crw-rw----  1 root scanner 21,   0 2008-06-19 17:34 /dev/sg0
crw-rw----  1 root cdrom   21,   1 2008-06-19 17:34 /dev/sg1
crw-rw----  1 root cdrom   21,   2 2008-06-19 17:34 /dev/sg2
crw-rw----  1 root disk    21,   3 2008-06-19 17:34 /dev/sg3
crw-rw----  1 root disk    21,   4 2008-06-19 17:34 /dev/sg4
crw-rw----  1 root scanner 21,   5 2008-06-19 17:34 /dev/sg5


Dual booting into an alternate OS proves that the hardware works with that OS. Could it be an interrupt conflict? Just grasping at straws....

---

### Post by tmastran on 2008-07-06
> **tmastran said:**
> 

Dual booting into an alternate OS proves that the hardware works with that OS. Could it be an interrupt conflict? Just grasping at straws....

After re-booting back into Ubuntu, I plugged in the USB device and it worked. A thumbdrive icon was even placed on the desktop (kde). This is bizarre? 

Here's the dmesg output now:

[  217.965913] usb 5-7: new high speed USB device using ehci_hcd and address 2
[  218.108463] usb 5-7: configuration #1 chosen from 1 choice
[  218.198591] usbcore: registered new interface driver libusual
[  218.225557] Initializing USB Mass Storage driver...
[  218.229049] scsi6 : SCSI emulation for USB Mass Storage devices
[  218.231100] usbcore: registered new interface driver usb-storage
[  218.231110] USB Mass Storage support registered.
[  218.231837] usb-storage: device found at 2
[  218.231843] usb-storage: waiting for device to settle before scanning
[  223.219049] usb-storage: device scan complete
[  223.245489] scsi 6:0:0:0: Direct-Access     Generic  STORAGE DEVICE   1.00 PQ: 0 ANSI: 0
[  223.247351] sd 6:0:0:0: [sdc] 251904 512-byte hardware sectors (129 MB)
[  223.252597] sd 6:0:0:0: [sdc] Write Protect is off
[  223.252608] sd 6:0:0:0: [sdc] Mode Sense: 02 00 00 00
[  223.252614] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[  223.255569] sd 6:0:0:0: [sdc] 251904 512-byte hardware sectors (129 MB)
[  223.256579] sd 6:0:0:0: [sdc] Write Protect is off
[  223.256588] sd 6:0:0:0: [sdc] Mode Sense: 02 00 00 00
[  223.256592] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[  223.257291]  sdc: sdc1
[  223.259127] sd 6:0:0:0: [sdc] Attached SCSI removable disk
[  223.259513] sd 6:0:0:0: Attached scsi generic sg6 type 0

Before it stopped at this line, just short of initializing the mass storage driver:

[  218.108463] usb 5-7: configuration #1 chosen from 1 choice

It mounted device:
/dev/sdc1             123M     0  123M   0% /media/LEXAR MEDIA

diff of after and after2 now shows:

diff after after2
41,47d40
< loop1
< loop2
< loop3
< loop4
< loop5
< loop6
< loop7
350a344,345
> sdc
> sdc1
358a354
> sg6
703a700,702
> usbdev5.2_ep00
> usbdev5.2_ep02
> usbdev5.2_ep81
705a705,710
> vcs2
> vcs3
> vcs4
> vcs5
> vcs6
> vcs7
708a714,719
> vcsa2
> vcsa3
> vcsa4
> vcsa5
> vcsa6
> vcsa7

So the sdc and sdc1 devices were created???

Still confused....

---

### Post by pytheas22 on 2008-07-06
> 
After re-booting back into Ubuntu, I plugged in the USB device and it worked. A thumbdrive icon was even placed on the desktop (kde). This is bizarre?

Yeah, that's really strange.  The only thing I can think of is that Windows (which I assume is your alternate operating system) is powering down or suspending the USB bus, or part of it, and Ubuntu is unable to wake it back up.  I have heard of problems like this with a couple kinds of ethernet cards--Windows will suspend them in such a way that only Windows can bring them back up.  But I have no idea if the same thing could occur for USB devices.  I know it doesn't make a lot of sense--especially because it appears that the USB bus is working fine even when devices attached through it are failing to mount--but I don't know what else to think.

Have you tried plugging stuff into all the different USB ports on your computer to see if it makes a difference?  Also, if you happen to have a PCI card with USB jacks, maybe you could try plugging that in...if Windows is powering down the USB bus on your motherboard somehow, this could help.

Otherwise, I don't know...maybe you can try reproducing the behavior (having the USB device work after booting from another operating system) just to make sure that there's really a relationship between the two.

---

### Post by tmastran on 2008-07-06
> **pytheas22 said:**
> Yeah, that's really strange.  The only thing I can think of is that Windows (which I assume is your alternate operating system) is powering down or suspending the USB bus, or part of it, and Ubuntu is unable to wake it back up.  I have heard of problems like this with a couple kinds of ethernet cards--Windows will suspend them in such a way that only Windows can bring them back up.  But I have no idea if the same thing could occur for USB devices.  I know it doesn't make a lot of sense--especially because it appears that the USB bus is working fine even when devices attached through it are failing to mount--but I don't know what else to think.

Have you tried plugging stuff into all the different USB ports on your computer to see if it makes a difference?  Also, if you happen to have a PCI card with USB jacks, maybe you could try plugging that in...if Windows is powering down the USB bus on your motherboard somehow, this could help.

Otherwise, I don't know...maybe you can try reproducing the behavior (having the USB device work after booting from another operating system) just to make sure that there's really a relationship between the two.

Thanks for your help, for now it still seems to mount my USB device, 24 hours after the reboot.

---

