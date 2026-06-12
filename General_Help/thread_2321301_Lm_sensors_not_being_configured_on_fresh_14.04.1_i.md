---
title: "Lm sensors not being configured on fresh 14.04.1 install"
date: 2016-04-21
forum: General Help
---

### Post by SagaciousKJB on 2016-04-21
I just got done installing a fresh version of Xubuntu 14.04.1 after upgrading to 12.04 left me with a really wonky system.  I installed lm-sensors and ran the usual sensors-detect, let it add the modules to the list automatically ( and restarted ) but it still doesn't show my sensors, which is really weird because the version of 14.04 I upgraded to shows them just fine as did 12.04.  I even copied the contents of /etc/sensors3.conf and /etc/sensors.d from the old 14.04 install to the new one and it doesn't appear to have any efffect.  This is very frustrating because there's seemingly no reason why they shouldn't be working just the way they did before.

---

### Post by SagaciousKJB on 2016-04-21
Output of sensors-detect
```
 sensors-detect revision 6170 (2013-05-20 21:25:22 +0200)
# System: Unknow Unknow [Unknow]
# Board: DFI Inc. LP JR 790GX

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

Some south bridges, CPUs or memory controllers contain embedded sensors.
Do you want to scan for them? This is totally safe. (YES/no): 
Module cpuid loaded successfully.
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD Family 10h thermal sensors...                           No
AMD Family 11h thermal sensors...                           No
AMD Family 12h and 14h thermal sensors...                   No
AMD Family 15h thermal sensors...                           No
AMD Family 15h power sensors...                             No
AMD Family 16h power sensors...                             No
Intel digital thermal sensor...                             No
Intel AMB FB-DIMM thermal sensor...                         No
VIA C7 thermal sensor...                                    No
VIA Nano thermal sensor...                                  No

Some Super I/O chips contain embedded sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): 
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor/ITE'...               No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               No
Trying family `ITE'...                                      Yes
Found `ITE IT8716F Super IO Sensors'                        Success!
    (address 0x228, driver `it87')
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor/ITE'...               No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               No
Trying family `ITE'...                                      No

Some systems (mainly servers) implement IPMI, a set of common interfaces
through which system health data may be retrieved, amongst other things.
We first try to get the information from SMBIOS. If we don't find it
there, we have to read from arbitrary I/O ports to probe for such
interfaces. This is normally safe. Do you want to scan for IPMI
interfaces? (YES/no): 
Probing for `IPMI BMC KCS' at 0xca0...                      No
Probing for `IPMI BMC SMIC' at 0xca8...                     No

Some hardware monitoring chips are accessible through the ISA I/O ports.
We have to write to arbitrary I/O ports to probe them. This is usually
safe though. Yes, you do have ISA I/O ports even if you do not have any
ISA slots! Do you want to scan the ISA I/O ports? (yes/NO): 

Lastly, we can probe the I2C/SMBus adapters for connected hardware
monitoring devices. This is the most risky part, and while it works
reasonably well on most systems, it has been reported to cause trouble
on some systems.
Do you want to probe the I2C/SMBus adapters now? (YES/no): 
Using driver `i2c-piix4' for device 0000:00:14.0: ATI Technologies Inc SB600/SB700/SB800 SMBus
Module i2c-dev loaded successfully.

Next adapter: cx18 i2c driver #0-0 (i2c-0)
Do you want to scan it? (yes/NO/selectively): 

Next adapter: cx18 i2c driver #0-1 (i2c-1)
Do you want to scan it? (yes/NO/selectively): 

Next adapter: NVIDIA i2c adapter  (i2c-2)
Do you want to scan it? (yes/NO/selectively): 

Next adapter: NVIDIA i2c adapter  (i2c-3)
Do you want to scan it? (yes/NO/selectively): 

Next adapter: NVIDIA i2c adapter  (i2c-4)
Do you want to scan it? (yes/NO/selectively): 

Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `it87':
  * ISA bus, address 0x228
    Chip `ITE IT8716F Super IO Sensors' (confidence: 9)

To load everything that is needed, add this to /etc/modules:
#----cut here----
# Chip drivers
it87
#----cut here----
If you have some drivers built into your kernel, the list above will
contain too many modules. Skip the appropriate ones!

Do you want to add these lines automatically to /etc/modules? (yes/NO)YES
Successful!

Monitoring programs won't work until the needed modules are
loaded. You may want to run 'service kmod start'
to load them.

Unloading i2c-dev... OK
Unloading cpuid... OK
```

Output of sensors
```

acpitz-virtual-0
Adapter: Virtual device
temp1:        +53.0°C  (crit = +84.0°C)

```

/etc/modules...

```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
# Parameters can be specified after the module name.

lp
rtc

# Generated by sensors-detect on Thu Apr 21 16:34:08 2016
# Chip drivers
it87

# Generated by sensors-detect on Thu Apr 21 17:38:59 2016
# Chip drivers
it87

# Generated by sensors-detect on Thu Apr 21 17:42:25 2016
# Chip drivers
it87

# Generated by sensors-detect on Thu Apr 21 18:23:22 2016
# Chip drivers
it87

```

Output of lsmod
```
Module                  Size  Used by
usblp                  22891  0 
bnep                   19624  2 
rfcomm                 69160  0 
bluetooth             391196  10 bnep,rfcomm
nvidia               8118098  34 
cx18_alsa              13730  1 
mxl5005s               54281  1 
s5h1409                18550  1 
tuner_simple           22368  1 
tuner_types            24636  1 tuner_simple
cs5345                 13014  1 
tda9887                13906  1 
tda8290                22428  0 
ir_lirc_codec          13021  0 
lirc_dev               19980  1 ir_lirc_codec
ir_rc6_decoder         12874  0 
ir_sony_decoder        12713  0 
ir_sanyo_decoder       12839  0 
ir_mce_kbd_decoder     13214  0 
ir_nec_decoder         12915  0 
ir_rc5_decoder         12710  0 
ir_jvc_decoder         12751  0 
tuner                  27308  2 
rc_rc6_mce             12502  0 
mceusb                 21980  0 
rc_core                28124  12 lirc_dev,ir_lirc_codec,ir_rc5_decoder,ir_nec_decoder,ir_sony_decoder,mceusb,ir_mce_kbd_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_sanyo_decoder,rc_rc6_mce
cx18                  131667  1 cx18_alsa
joydev                 17381  0 
videobuf_vmalloc       13589  1 cx18
tveeprom               21216  1 cx18
snd_hda_codec_realtek    61438  1 
cx2341x                28230  1 cx18
snd_hda_intel          52355  3 
dvb_core              121659  1 cx18
snd_hda_codec         192906  2 snd_hda_codec_realtek,snd_hda_intel
v4l2_common            15681  4 cx18,cx2341x,tuner,cs5345
snd_hwdep              13602  1 snd_hda_codec
videobuf_core          26023  2 cx18,videobuf_vmalloc
snd_pcm               102099  3 cx18_alsa,snd_hda_codec,snd_hda_intel
videodev              134688  5 cx18,cx2341x,tuner,cs5345,v4l2_common
kvm                   451511  0 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
i2c_algo_bit           13413  1 cx18
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
serio_raw              13462  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
edac_core              62291  0 
snd                    69238  19 snd_hda_codec_realtek,cx18_alsa,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
edac_mce_amd           22617  0 
soundcore              12680  1 snd
k10temp                13126  0 
shpchp                 37032  0 
i2c_piix4              22155  0 
wmi                    19177  0 
mac_hid                13205  0 
parport_pc             32701  0 
ppdev                  17671  0 
hwmon_vid              12783  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
hid_generic            12548  0 
usbhid                 52570  0 
hid                   106148  2 hid_generic,usbhid
pata_acpi              13038  0 
psmouse               106678  0 
pata_atiixp            13271  3 
ahci                   25819  3 
sky2                   58191  0 
libahci                32560  1 ahci
floppy                 69418  0
```

---

### Post by SagaciousKJB on 2016-04-21
I noticed that it87 wasn't actually listed...

sudo modprobe it87
```
modprobe: ERROR: could not insert 'it87': Device or resource busy

```

dmesg entry
```

[ 2849.946419] it87: Found IT8716F chip at 0x228, revision 3
[ 2849.946489] ACPI Warning: 0x000000000000022d-0x000000000000022e SystemIO conflicts with Region \IP__ 1 (20131115/utaddress-251)
[ 2849.946499] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
```

---

