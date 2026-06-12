---
title: "Large pause at start of boot time, possibly modprobe related"
date: 2007-03-18
forum: General Help
---

### Post by timothyM on 2007-03-18
Hello,

Whenever I boot my computer, it gets to the boot splash screen fine, but after the first increment on the status bar, it hangs at that points for 20-25s, before it continues with the rest of the boot process.

I have installed bootchart, and at that corresponding interval there appears to be a area of zero activity, and modprobe appears to be on unint sleep. (See attached file)

I've checked my /var/log/boot, and that appears ok with no errors, and dmesg | grep error gives several:

```
[17179596.024000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[17179596.024000] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[17179596.024000] end_request: I/O error, dev hdc, sector 863872
[17179596.024000] Buffer I/O error on device hdc, logical block 215968

```

as well as:
```

[17179593.804000] usb 1-1: device not accepting address 2, error -71
[17179610.180000] VIA 82xx Modem: probe of 0000:00:11.6 failed with error -13
```

Are these related to my problem, or does anyone have any ideas of how to solve this?

Many Thanks,

Timothy

---

