---
title: "CD burning?"
date: 2007-10-31
forum: General Help
---

### Post by Dvorakis on 2007-10-31
It won't let me burn a CD,even though my CD burner worked fine in windows.
It also just lets me Read CD's,so I can read CD's fine,but it won't burn them.

---

### Post by skyjacker on 2007-10-31
> **Dvorakis said:**
> It won't let me burn a CD,even though my CD burner worked fine in windows.
It also just lets me Read CD's,so I can read CD's fine,but it won't burn them.Need some more information if you want us to help you. What cd burner are you trying to use? Do you have ubuntu, kubuntu,what desktop?

---

### Post by ofb on 2007-10-31
That's odd. Try K3B as an experiment. For me it resurrected two old burners that no longer worked under Nero.

---

### Post by Maestro23 on 2007-10-31
> **ofb said:**
> That's odd. Try K3B as an experiment. For me it resurrected two old burners that no longer worked under Nero.

I run Gnome and K3B has never let me down yet.  Just my personal experience with it.:popcorn:

---

### Post by Dvorakis on 2007-11-02
I head K3B was good,but it still doesn't work for me.
My CD burner is,CD058D Atapi cd-R/RW.It came with my computer,so Im not exactly sure on it.
When I use KD3 It gives me the error.
CDRECORD Has no permission to open the device.

---

### Post by Dvorakis on 2007-11-02
OK update,when I try to run Sudo k3b I get this 

```
dvorak@dvorak-ubuntu:~$ sudo k3b
X Error: BadDevice, invalid or uninitialized input device 171
  Major opcode:  149
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 171
  Major opcode:  149
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
ERROR: Communication problem with k3b, it probably crashed.
dvorak@dvorak-ubuntu:~$ kdecore (KAction): WARNING: KActionCollection::KActionCollection( QObject *parent, const char *name, KInstance *instance )
(K3bDevice::HalConnection) initializing HAL >= 0.5
Mapping udi /org/freedesktop/Hal/devices/storage_serial_NC000000Q0 to device /dev/hdc
/dev/hdc resolved to /dev/hdc
/dev/hdc is block device (0)
/dev/hdc seems not to be a cdrom device: Resource temporarily unavailable
/dev/hdc resolved to /dev/hdc
/dev/hdc is block device (0)
/dev/hdc seems not to be a cdrom device: Resource temporarily unavailable
Devices:
------------------------------
kdecore (KAction): WARNING: KActionCollection::operator+=(): function is severely deprecated.
Error: "/var/tmp/kdecache-dvorak" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-dvorak" is owned by uid 1000 instead of uid 0.
Error: "/tmp/ksocket-dvorak" is owned by uid 1000 instead of uid 0.

```

---

### Post by Sef on 2007-11-02
I've had problems with K3b too.  Now I use Gnomebaker, and it burns just fine.  It is  installed by default under Applications > Sound & Video.  (If it is not, then download it from the repositories.)

---

### Post by ofb on 2007-11-02
Might be best to start with the first error, fix it, then run again to see what errors remain.

What OS are you running Dvorakis? This one was supposed to be fixed in Gutsy,
[https://bugs.launchpad.net/ubuntu/+source/wacom-tools/+bug/42553](https://bugs.launchpad.net/ubuntu/+source/wacom-tools/+bug/42553)

---

### Post by Dvorakis on 2007-11-04
Gutsy,Its still a problem with me though.

I've tried gnomebaker too,i've basically tried everyone out thier...but with no avail.

---

### Post by ofb on 2007-11-04
I've noticed a few posts about not being able to burn in 7.10 now, but no solutions yet.

Do you have those wacom lines in xorg.conf that they're talking about? My main machine actually uses a wacom. Just firing up the other box with Edubuntu 7.10 now... and yep, they're still there on that one, but commented out now by default.

Trying a burn... Oh, nasty. I can read the CDRW in K3B but can't mount it to erase. Here's the output from starting it via terminal.

```
o@bluefish:~$ k3b
o@bluefish:~$ kdecore (KAction): WARNING: KActionCollection::KActionCollection( QObject *parent, const char *name, KInstance *instance )
(K3bDevice::HalConnection) initializing HAL >= 0.5
Mapping udi /org/freedesktop/Hal/devices/storage_model_CREATIVE_CD_RW_RW4224E to device /dev/hdd
Mapping udi /org/freedesktop/Hal/devices/storage_model_ASUS_CD_S520/A to device /dev/hdc
/dev/hdc resolved to /dev/hdc
/dev/hdc is block device (0)
/dev/hdc seems to be cdrom
(K3bDevice::Device) /dev/hdc: init()
(K3bDevice::ScsiCommand) failed: 
                           command:    GET CONFIGURATION (46)
                           errorcode:  70
                           sense key:  NOT READY (2)
                           asc:        3a
                           ascq:       0
(K3bDevice::ScsiCommand) failed: 
                           command:    GET CONFIGURATION (46)
                           errorcode:  70
                           sense key:  NOT READY (2)
                           asc:        3a
                           ascq:       0
(K3bDevice::ScsiCommand) failed: 
                           command:    GET CONFIGURATION (46)
                           errorcode:  70
                           sense key:  NOT READY (2)
                           asc:        3a
                           ascq:       0
(K3bDevice::ScsiCommand) failed: 
                           command:    GET CONFIGURATION (46)
                           errorcode:  70
                           sense key:  NOT READY (2)
                           asc:        3a
                           ascq:       0
(K3bDevice::ScsiCommand) failed: 
                           command:    GET CONFIGURATION (46)
                           errorcode:  70
                           sense key:  NOT READY (2)
                           asc:        3a
                           ascq:       0
(K3bDevice::ScsiCommand) failed: 
                           command:    GET CONFIGURATION (46)
                           errorcode:  70
                           sense key:  NOT READY (2)
                           asc:        3a
                           ascq:       0
(K3bDevice::ScsiCommand) failed: 
                           command:    GET CONFIGURATION (46)
                           errorcode:  70
                           sense key:  NOT READY (2)
                           asc:        3a
                           ascq:       0
(K3bDevice::ScsiCommand) failed: 
                           command:    GET CONFIGURATION (46)
                           errorcode:  70
                           sense key:  NOT READY (2)
                           asc:        3a
                           ascq:       0
(K3bDevice::ScsiCommand) failed: 
                           command:    GET CONFIGURATION (46)
                           errorcode:  70
                           sense key:  NOT READY (2)
                           asc:        3a
                           ascq:       0
(K3bDevice::ScsiCommand) failed: 
                           command:    GET CONFIGURATION (46)
                           errorcode:  70
                           sense key:  NOT READY (2)
                           asc:        3a
                           ascq:       0
(K3bDevice::ScsiCommand) failed: 
                           command:    GET CONFIGURATION (46)
                           errorcode:  70
                           sense key:  NOT READY (2)
                           asc:        3a
                           ascq:       0
(K3bDevice::ScsiCommand) failed: 
                           command:    GET CONFIGURATION (46)
                           errorcode:  70
                           sense key:  NOT READY (2)
                           asc:        3a
                           ascq:       0
(K3bDevice::ScsiCommand) failed: 
                           command:    GET CONFIGURATION (46)
                           errorcode:  70
                           sense key:  NOT READY (2)
                           asc:        3a
                           ascq:       0
(K3bDevice::ScsiCommand) failed: 
                           command:    GET CONFIGURATION (46)
                           errorcode:  70
                           sense key:  NOT READY (2)
                           asc:        3a
                           ascq:       0
(K3bDevice::ScsiCommand) failed: 
                           command:    GET CONFIGURATION (46)
                           errorcode:  70
                           sense key:  NOT READY (2)
                           asc:        3a
                           ascq:       0
(K3bDevice::ScsiCommand) failed: 
                           command:    MODE SENSE (5a)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        24
                           ascq:       0
(K3bDevice::Device) /dev/hdc: MODE SENSE length det failed.
(K3bDevice::ScsiCommand) failed: 
                           command:    MODE SENSE (5a)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        24
                           ascq:       0
(K3bDevice::Device) /dev/hdc: MODE SENSE with real length 65535 failed.
(K3bDevice::Device) /dev/hdc: modeSense 0x05 failed!
(K3bDevice::Device) /dev/hdc: Cannot check write modes.
(K3bDevice::ScsiCommand) failed: 
                           command:    MODE SENSE (5a)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        24
                           ascq:       0
(K3bDevice::Device) /dev/hdc: MODE SENSE length det failed.
(K3bDevice::ScsiCommand) failed: 
                           command:    MODE SENSE (5a)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        24
                           ascq:       0
(K3bDevice::Device) /dev/hdc: MODE SENSE with real length 65535 failed.
/dev/hdd resolved to /dev/hdd
/dev/hdd is block device (64)
/dev/hdd seems to be cdrom
(K3bDevice::Device) /dev/hdd: init()
(K3bDevice::ScsiCommand) failed: 
                           command:    GET CONFIGURATION (46)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        20
                           ascq:       0
(K3bDevice::ScsiCommand) failed: 
                           command:    GET CONFIGURATION (46)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        20
                           ascq:       0
(K3bDevice::ScsiCommand) failed: 
                           command:    GET CONFIGURATION (46)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        20
                           ascq:       0
(K3bDevice::ScsiCommand) failed: 
                           command:    GET CONFIGURATION (46)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        20
                           ascq:       0
(K3bDevice::ScsiCommand) failed: 
                           command:    GET CONFIGURATION (46)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        20
                           ascq:       0
(K3bDevice::ScsiCommand) failed: 
                           command:    GET CONFIGURATION (46)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        20
                           ascq:       0
(K3bDevice::ScsiCommand) failed: 
                           command:    GET CONFIGURATION (46)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        20
                           ascq:       0
(K3bDevice::ScsiCommand) failed: 
                           command:    GET CONFIGURATION (46)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        20
                           ascq:       0
(K3bDevice::ScsiCommand) failed: 
                           command:    GET CONFIGURATION (46)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        20
                           ascq:       0
(K3bDevice::ScsiCommand) failed: 
                           command:    GET CONFIGURATION (46)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        20
                           ascq:       0
(K3bDevice::ScsiCommand) failed: 
                           command:    GET CONFIGURATION (46)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        20
                           ascq:       0
(K3bDevice::ScsiCommand) failed: 
                           command:    GET CONFIGURATION (46)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        20
                           ascq:       0
(K3bDevice::ScsiCommand) failed: 
                           command:    GET CONFIGURATION (46)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        20
                           ascq:       0
(K3bDevice::ScsiCommand) failed: 
                           command:    GET CONFIGURATION (46)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        20
                           ascq:       0
(K3bDevice::ScsiCommand) failed: 
                           command:    GET CONFIGURATION (46)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        20
                           ascq:       0
(K3bDevice::Device) /dev/hdd: dataLen: 60
(K3bDevice::Device) /dev/hdd: checking for TAO
(K3bDevice::Device) /dev/hdd: checking for SAO
(K3bDevice::Device) /dev/hdd: checking for SAO_R96P
(K3bDevice::Device) /dev/hdd: checking for SAO_R96R
(K3bDevice::Device) /dev/hdd: checking for RAW_R16
(K3bDevice::Device) /dev/hdd: checking for RAW_R96P
(K3bDevice::Device) /dev/hdd: checking for RAW_R96R
(K3bDevice::ScsiCommand) failed: 
                           command:    GET CONFIGURATION (46)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        20
                           ascq:       0
(K3bDevice::Device) /dev/hdd GET_CONFIGURATION failed.
(K3bDevice::ScsiCommand) failed: 
                           command:    READ DVD STRUCTURE (ad)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        20
                           ascq:       0
(K3bDevice::Device) /dev/hdd: READ DVD STRUCTURE length det failed
(K3bDevice::ScsiCommand) failed: 
                           command:    READ DVD STRUCTURE (ad)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        20
                           ascq:       0
(K3bDevice::Device) /dev/hdd: READ DVD STRUCTURE length det failed
(K3bDevice::Device) /dev/hdd: READ TOC/PMA/ATIP invalid length returned: 4
(K3bDevice::ScsiCommand) failed: 
                           command:    MODE SENSE (5a)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        24
                           ascq:       0
(K3bDevice::Device) /dev/hdd: MODE SENSE length det failed.
(K3bDevice::ScsiCommand) failed: 
                           command:    MODE SENSE (5a)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        24
                           ascq:       0
(K3bDevice::Device) /dev/hdd: MODE SENSE with real length 65535 failed.
(K3bDevice::DeviceManager) setting current write speed of device /dev/hdd to 353
Could not resolve /dev/scd0
/dev/scd0 resolved to /dev/scd0
(K3bDevice::Device) could not open device /dev/scd0 for reading
                    (No such file or directory)
could not open device /dev/scd0 (No such file or directory)
/dev/hdc resolved to /dev/hdc
(K3bDevice::DeviceManager) dev /dev/hdc already found
/dev/hdd resolved to /dev/hdd
(K3bDevice::DeviceManager) dev /dev/hdd already found
(K3bDevice::DeviceManager) found config entry for devicetype: ASUS CD-S520/A
(K3bDevice::DeviceManager) found config entry for devicetype: CREATIVE CD-RW RW4224E
(K3bDevice::ScsiCommand) failed: 
                           command:    GET CONFIGURATION (46)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        20
                           ascq:       0
(K3bDevice::Device) /dev/hdd GET_CONFIGURATION failed.
(K3bDevice::Device) /dev/hdd: Device reports bogus disc information length of 2
(K3bDevice::ScsiCommand) failed: 
                           command:    GET CONFIGURATION (46)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        20
                           ascq:       0
(K3bDevice::Device) /dev/hdd GET_CONFIGURATION failed.
(K3bDevice::ScsiCommand) failed: 
                           command:    READ DVD STRUCTURE (ad)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        20
                           ascq:       0
(K3bDevice::Device) /dev/hdd: READ DVD STRUCTURE length det failed
(K3bDevice::ScsiCommand) failed: 
                           command:    READ DVD STRUCTURE (ad)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        20
                           ascq:       0
(K3bDevice::Device) /dev/hdd: READ DVD STRUCTURE length det failed
(K3bDevice::Device) /dev/hdd: READ TOC/PMA/ATIP invalid length returned: 4
(K3bDevice::ScsiCommand) failed: 
                           command:    GET CONFIGURATION (46)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        20
                           ascq:       0
(K3bDevice::Device) /dev/hdd GET_CONFIGURATION failed.
(K3bDevice::ScsiCommand) failed: 
                           command:    READ DVD STRUCTURE (ad)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        20
                           ascq:       0
(K3bDevice::Device) /dev/hdd: READ DVD STRUCTURE length det failed
Devices:
------------------------------
Blockdevice:    /dev/hdc
Generic device: 
Vendor:         ASUS
Description:    CD-S520/A
Version:        1.9K
Write speed:    0
Profiles:       Error
Read Cap:       CD-ROM
Write Cap:      Error
Writing modes:  None
Reader aliases: /dev/hdc
------------------------------
Blockdevice:    /dev/hdd
Generic device: 
Vendor:         CREATIVE
Description:    CD-RW RW4224E
Version:        1.36
Write speed:    353
Profiles:       Error
Read Cap:       CD-ROM, CD-R, CD-RW
Write Cap:      CD-R, CD-RW
Writing modes:  SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R
Reader aliases: /dev/hdd
------------------------------
kdecore (KAction): WARNING: KActionCollection::operator+=(): function is severely deprecated.
(K3bDevice::ScsiCommand) failed: 
                           command:    READ DVD STRUCTURE (ad)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        20
                           ascq:       0
(K3bDevice::Device) /dev/hdd: READ DVD STRUCTURE length det failed
(K3bDevice::Device) /dev/hdd: READ TOC/PMA/ATIP invalid length returned: 4
DiskInfo:
Mediatype:       CD-RW
Current Profile: Unknown
Disk state:      incomplete
Empty:           0
Rewritable:      1
Appendable:      1
Sessions:        1
Tracks:          1
Layers:          1
Capacity:        74:10:00 (LBA 333750) (683520000 Bytes)
Remaining size:  47:59:11 (LBA 215936) (442236928 Bytes)
Used Size:       26:10:64 (LBA 117814) (241283072 Bytes)
(K3bDevice::ScsiCommand) failed: 
                           command:    GET CONFIGURATION (46)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        20
                           ascq:       0
(K3bDevice::Device) /dev/hdd GET_CONFIGURATION failed.
(K3bDevice::ScsiCommand) failed: 
                           command:    READ DVD STRUCTURE (ad)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        20
                           ascq:       0
(K3bDevice::Device) /dev/hdd: READ DVD STRUCTURE length det failed
(K3bDevice::ScsiCommand) failed: 
                           command:    READ DVD STRUCTURE (ad)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        20
                           ascq:       0
(K3bDevice::Device) /dev/hdd: READ DVD STRUCTURE length det failed
(K3bDevice::Device) /dev/hdd: READ TOC/PMA/ATIP invalid length returned: 4
(K3bDevice::ScsiCommand) failed: 
                           command:    GET CONFIGURATION (46)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        20
                           ascq:       0
(K3bDevice::Device) /dev/hdd GET_CONFIGURATION failed.
Session |  ADR   | CONTROL|  TNO   | POINT  |  Min   |  Sec   | Frame  |  Zero  |  PMIN  |  PSEC  | PFRAME |
      1 |      1 |      4 |      0 |     a0 |      0 |      0 |      0 |      0 |      1 |     32 |      0 |
      1 |      1 |      4 |      0 |     a1 |      0 |      0 |      0 |      0 |      1 |      0 |      0 |
      1 |      1 |      4 |      0 |     a2 |      0 |      0 |      0 |      0 |      1 |    194 |    214 |
      1 |      1 |      4 |      0 |      1 |      0 |      0 |      0 |      0 |      0 |      0 |      0 |
      1 |      5 |      4 |      0 |     b0 |      1 |    238 |    200 |      3 |      5 |     23 |    182 |
      1 |      5 |      4 |      0 |     c0 |    102 |      0 |    156 |      0 |      6 |    176 |    103 |
      1 |      5 |      4 |      0 |     c1 |     72 |     52 |    176 |      0 |      0 |      0 |      0 |
(K3bDevice::Device) found invalid bcd values. No bcd toc.
(K3bDevice::Device) found invalid hex values. No hex toc.
(K3bDevice::Device) unable to determine if hex (1) or bcd (1).
(K3bDevice::ScsiCommand) failed: 
                           command:    GET CONFIGURATION (46)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        20
                           ascq:       0
(K3bDevice::Device) /dev/hdd GET_CONFIGURATION failed.
(K3bDevice::ScsiCommand) failed: 
                           command:    READ DVD STRUCTURE (ad)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        20
                           ascq:       0
(K3bDevice::Device) /dev/hdd: READ DVD STRUCTURE length det failed
(K3bDevice::ScsiCommand) failed: 
                           command:    READ DVD STRUCTURE (ad)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        20
                           ascq:       0
(K3bDevice::Device) /dev/hdd: READ DVD STRUCTURE length det failed
(K3bDevice::Device) /dev/hdd: READ TOC/PMA/ATIP invalid length returned: 4
(K3bDevice::ScsiCommand) failed: 
                           command:    GET CONFIGURATION (46)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        20
                           ascq:       0
(K3bDevice::Device) /dev/hdd GET_CONFIGURATION failed.
(K3bDevice::ScsiCommand) failed: 
                           command:    READ DVD STRUCTURE (ad)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        20
                           ascq:       0
(K3bDevice::Device) /dev/hdd: READ DVD STRUCTURE length det failed
(K3bDevice::ScsiCommand) failed: 
                           command:    READ DVD STRUCTURE (ad)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        20
                           ascq:       0
(K3bDevice::Device) /dev/hdd: READ DVD STRUCTURE length det failed
(K3bDevice::Device) /dev/hdd: READ TOC/PMA/ATIP invalid length returned: 4
(K3bDevice::ScsiCommand) failed: 
                           command:    GET PERFORMANCE (ac)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        20
                           ascq:       0
(K3bDevice::Device) /dev/hdd: GET PERFORMANCE length det failed.
```

Yet there's no problem erasing and writing with K3B on my main Ubuntu 7.10.

---

### Post by masmre on 2007-11-04
Possible  workaround  (i.e. telling k3b to use the dev=/dev/cdrw option) goes like this:

    k3b > settings > configure k3b > Programs > User Parameters
    there type in dev=/dev/cdrw in the line cdrecord 

kredits to : [http://www.umsu.de/magdalena/archiv/1158052560](http://www.umsu.de/magdalena/archiv/1158052560) 
:)

---

### Post by Dvorakis on 2007-11-04
Still no luck.Im getting some different errors every once and a while...but I still get the same Cdrecord has no permission to open the device most of the time.

Any help anyone?

---

### Post by Micronot on 2007-11-08
I don't know the answer.  I run Dapper/gnome. I'm completely up to date on updates. I have a data DVD that i've copied to my desktop. so I could then write smaller chunks of data to a cd (700mb cd vs. 15+gig dvd). 
  I put a cd-r in my cd-write drive. The disc is completely blank.. No matter what I try I can't copy any info to my cd-r. The cdrecorder always says "Error- you don't have permission to write to this folder" When I go to properties & try to change the associated permissions, I'm notified that I can't becuase it's a read only disc. urrrgh

---

