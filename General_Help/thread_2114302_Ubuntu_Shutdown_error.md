---
title: "Ubuntu Shutdown error"
date: 2013-02-09
forum: General Help
---

### Post by cyanide911 on 2013-02-09
I get this error sometimes when I shut down my Ubuntu 12.04:
[IMG]http://i.imgur.com/ibRteXZ.jpg?1[/IMG]

Any clue how to fix this?

---

### Post by Jay Christnach on 2013-02-09
I think you can ignore the message. It does no harm. It merely tells you that the wireless adapter doesn't support a power off (or whatever) request. Some ACPI function. Those are known to often be not supported by the hardware.  Hopefully your computer switches off as you told it to do so.

---

### Post by cyanide911 on 2013-02-10
> **Jay Christnach said:**
> I think you can ignore the message. It does no harm. It merely tells you that the wireless adapter doesn't support a power off (or whatever) request. Some ACPI function. Those are known to often be not supported by the hardware.  Hopefully your computer switches off as you told it to do so.

Um yeah I should've mentioned. It freezes at this screen. I've to manually turn it off by the power button.

---

### Post by cyanide911 on 2013-02-12
Any solutions to this problem?

---

### Post by slickymaster on 2013-02-12
Probably this has to do with the wireless drivers power management mode.
If you run:```
iwconfig wlan0
``` does it say **Power Management: on**?
If so, you might try:```
sudo iwconfig wlan0 power off
``` Does it help? If so, you can amend** /etc/rc.local** to make it permanent.

Place the command _before the exit 0 line_ in that file so that it looks like:
```
iwconfig wlan0 power off
exit 0
```

---

