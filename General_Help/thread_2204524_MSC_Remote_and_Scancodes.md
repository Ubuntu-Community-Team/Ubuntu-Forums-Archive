---
title: "MSC Remote and Scancodes"
date: 2014-02-08
forum: General Help
---

### Post by gregh2 on 2014-02-08
Hello,

I'm attempting to get a MSC-USB remote working in Ubuntu.  I've had this working before in previous versions of Ubuntu, but after a fresh install of Ubuntu 13.10 the remote doesn't work.  The specific model of the remote is HA-IR01SV(TSHA-IR01).  The receiver is plugged in, and every time I press a button the LED light is triggered.  I've also plugged the USB IR Receiver into a windows 7 computer and it works with that system.

When I test the remote with ir-keytable -t it appears to be capturing incomplete scan codes.  See below an example of the output of ir-keytable -t.  Note on the remote I only pressed the "play" button.  Each time I pressed it, I get a different scan code being displayed.  This appears to happen for any key I press.  It never gives the same value when I press it repeatedly.
```

Testing events. Please, press CTRL-C to abort.
1391920154.435603: event MSC: scancode = 200
1391920154.435603: event sync
1391920157.027579: event MSC: scancode = 4007c
1391920157.027579: event sync
1391920157.283549: event MSC: scancode = 400
1391920157.283549: event sync
1391920157.603557: event MSC: scancode = 2003c
1391920157.603557: event sync
1391920157.955557: event MSC: scancode = 100
1391920157.955557: event sync
1391920158.179538: event MSC: scancode = 1001f
1391920158.179538: event sync
1391920158.595544: event MSC: scancode = 100
1391920158.595544: event sync
1391920158.819545: event MSC: scancode = 1001e
1391920158.819545: event sync

```

I'm assuming this is why the remote isn't working.  That the scancodes are not the same, and do not match what they should be a this remote.  Any help in tracking down a solution to this would be greatly appreciated.

Here is the remote being reported by IR-keytable.
```

Found /sys/class/rc/rc3/ (/dev/input/event4) with:
        Driver mceusb, table rc-rc6-mce
        Supported protocols: NEC RC-5 RC-6 JVC SONY SANYO LIRC other
        Enabled protocols: RC-6
        Repeat delay = 500 ms, repeat period = 125 ms

```

Here is the output of lsusb:
```

lsusb
Bus 002 Device 002: ID 8087:8000 Intel Corp.
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp.
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 1784:0008 TopSeed Technology Corp. eHome Infrared Transceiver
Bus 003 Device 003: ID 0e8f:0020 GreenAsia Inc. USB to PS/2 Adapter
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Thanks for your time,
Greg

---

