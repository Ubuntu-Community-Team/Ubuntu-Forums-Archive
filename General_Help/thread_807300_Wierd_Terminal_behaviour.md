---
title: "Wierd Terminal behaviour"
date: 2008-05-25
forum: General Help
---

### Post by MaindotC on 2008-05-25
If I do:
```

cat /var/log/udev | more

```
I get usual output and character formatting up to this point:
```

DEVNAME=/dev/ptyb2

UDEV  [1211694287.442379] add      /block/sr0 (block)
UDEV_LOG=3
ACTION=add
DEVPATH=/block/sr0
SUBSYSTEM=block
SEQNUM=1819
MINOR=0
MAJOR=11
PHYSDEVPATH=/devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0
PHYSDEVBUS=scsi
PHYSDEVDRIVER=sr
UDEVD_EVENT=1
ID_CDROM=1
ID_CDROM_CD_R=1
ID_CDROM_CD_RW=1
ID_CDROM_DVD=1
ID_CDROM_DVD_R=1
ID_CDROM_DVD_RAM=1
ID_CDROM_MRW=1
ID_CDROM_MRW_W=1
ID_CDROM_RAM=1
DEVTYPE=disk
ID_VENDOR=MATSHITA
ID_MODEL=DVD-RAM_UJ-842
ID_REVISION=RB01
ID_SERIAL=
ID_SERIAL_SHORT=&#65533;S&#1911;à=¼ù·=²¿&#9500;>²¿!Ï_ý
ID_TYPE=&#9228;&#9229;
ID_BUS=&#9149;&#9228;&#9149;&#9227;
ID_PATH=&#9147;&#9228;&#9227;-0000:00:1°.2-&#9149;&#9228;&#9149;&#9227;-1:0:0:0
GENERATED=1
DEVNAME=/&#9229;&#9226;&#9524;/&#9149;&#9228;&#9229;0
DEVLINKS=/&#9229;&#9226;&#9524;/&#9149;&#9148;0 /&#9229;&#9226;&#9524;/&#9229;&#9227;&#9149;&#9488;/&#9225;&#8804;-&#9147;&#9618;&#9500;&#9252;/&#9147;&#9228;&#9227;-0000:00:1°.2-&#9149;&#9228;&#9149;&#9227;-1:0:0:0 /&#9229;&#9226;&#9524;/&#9228;&#9229;&#9148;&#9146;&#9492; /&#9229;&#9226;&#9524;/&#9228;&#9229;&#9148;&#9516; /&#9229;&#9226;&#9524;/&#9229;&#9524;&#9229; /&#9229;&#9226;&#9524;/&#9229;&#9524;&#9229;&#9148;&#9516;

UDEV  [1211694287.442423] &#9618;&#9229;&#9229;      /&#9228;&#9484;&#9618;&#9149;&#9149;/&#9500;&#9500;&#8804;/&#9147;&#9500;&#8804;&#9618;&#9229; (&#9500;&#9500;&#8804;)
UDEV_LOG=3
ACTION=&#9618;&#9229;&#9229;
DEVPATH=/&#9228;&#9484;&#9618;&#9149;&#9149;/&#9500;&#9500;&#8804;/&#9147;&#9500;&#8804;&#9618;&#9229;
SUBSYSTEM=&#9500;&#9500;&#8804;
SEQNUM=1877
MAJOR=2
MINOR=189
UDEVD_EVENT=1
DEVNAME=/&#9229;&#9226;&#9524;/&#9147;&#9500;&#8804;&#9618;&#9229;

```

Then see how all the characters go awry?  Here's what the terminal prompt looks like when it completes:
```

UDEV  [1211694290.855519] &#9618;&#9229;&#9229;      /&#9228;&#9484;&#9618;&#9149;&#9149;/&#9149;&#9146;&#9508;&#9532;&#9229;/&#9228;&#9146;&#9532;&#9500;&#9148;&#9146;&#9484;C0 (&#9149;&#9146;&#9508;&#9532;&#9229;)
UDEV_LOG=3
ACTION=&#9618;&#9229;&#9229;
DEVPATH=/&#9228;&#9484;&#9618;&#9149;&#9149;/&#9149;&#9146;&#9508;&#9532;&#9229;/&#9228;&#9146;&#9532;&#9500;&#9148;&#9146;&#9484;C0
SUBSYSTEM=&#9149;&#9146;&#9508;&#9532;&#9229;
SEQNUM=2700
MAJOR=116
MINOR=7
PHYSDEVPATH=/&#9229;&#9226;&#9524;&#9227;&#9228;&#9226;&#9149;/&#9147;&#9228;&#9227;0000:00/0000:00:1&#9225;.0
PHYSDEVBUS=&#9147;&#9228;&#9227;
PHYSDEVDRIVER=HDA I&#9532;&#9500;&#9226;&#9484;
UDEVD_EVENT=1
DEVNAME=/&#9229;&#9226;&#9524;/&#9149;&#9532;&#9229;/&#9228;&#9146;&#9532;&#9500;&#9148;&#9146;&#9484;C0

&#9618;34&#9484;&#9488;&#9496;2348&#9229;&#9149;°311@&#9618;34&#9484;&#9488;&#9496;2348&#9229;&#9149;°311-&#9484;&#9618;&#9147;&#9500;&#9146;&#9147;:/&#9524;&#9618;&#9148;/&#9484;&#9146;±$ 

```

It's probably dependent on a billion other factors but just thought I'd ask - why does this happen?

---

### Post by Monicker on 2008-05-25
Hrmm. The only time I've seen something like before is when I have accidentally piped a binary file to stdout.  Something in your initial output is probably being seen as control codes and throwing off the display afterwards.  You could try typing "reset" after you get the garbled text; that usually resolves it for me.

---

### Post by MaindotC on 2008-05-25
I'll do that.  It's not really a big inconvenience but I just thought it was interesting.

---

