---
title: "Lenovo G580 Brightness Problems Ubuntu 13.04 64-bit"
date: 2013-06-23
forum: General Help
---

### Post by ChillyCurve on 2013-06-23
I recently bought a new Lenovo G580, which came with Windows 8. I quickly replaced it with Ubuntu.

Everything works fine except my brightness control. The pop-up comes up and displays the brightness changing, when it actually isn't.

I have tried everything, and nothing works.

Thanks in advance for your help.

If you need me to post the results of any commands, just ask.

---

### Post by Toz on 2013-06-23
Enable the **acpi_osi=Linux** kernel parameter. See the "Kernel Boot Parameters" link in my signature for information on how to do this.

---

### Post by ChillyCurve on 2013-06-23
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux"

Is this right? It didn't work.

---

### Post by Toz on 2013-06-23
Did you run:
```
sudo update-grub
```
...and reboot afterwards?

Can you post back the results of:
```
cat /proc/cmdline
```
...and
```
lspci -vnn | grep VGA
```

---

### Post by ChillyCurve on 2013-06-23
Yes I did.

And this is the output I got:

```
~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.8.0-26-generic root=UUID=3ccaea53-207b-481b-844b-a769c7bc6899 ro quiet splash acpi_osi=Linux vt.handoff=7

```

---

### Post by Toz on 2013-06-23
Which video card do you have?
```
sudo lspci -vnn | grep -A12 VGA
```

Also:
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done
```

---

### Post by ChillyCurve on 2013-06-23
```
00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09) (prog-if 00 [VGA controller])
    Subsystem: Lenovo Device [17aa:3977]
    Flags: bus master, fast devsel, latency 0, IRQ 42
    Memory at f0000000 (64-bit, non-prefetchable) [size=4M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 3000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [d0] Power Management version 2
    Capabilities: [a4] PCI Advanced Features
    Kernel driver in use: i915

00:14.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller [8086:1e31] (rev 04) (prog-if 30 [XHCI])

```

and

```
/sys/class/backlight/acpi_video0
1
10
/sys/class/backlight/intel_backlight
4437
4437

```

---

### Post by Toz on 2013-06-23
Okay. Try this combination of kernel parameters:
```
acpi_osi=Linux acpi_backlight=vendor
```

---

### Post by ChillyCurve on 2013-06-23
Works, thank you so much.

But now my hotkey doesn't work.... Any ideas?

---

### Post by Toz on 2013-06-23
This ones funny. Try it with just:
```
acpi_backlight=vendor
```

---

### Post by ChillyCurve on 2013-06-23
Works like a charm, thanks :D

---

### Post by Toz on 2013-06-24
> **ChillyCurve said:**
> Works like a charm, thanks :D

Glad to hear. Can you mark this thread as SOLVED by:
1. Click on the "Edit Post" link in your first post.
2. Click on "Go Advanced"
3. Change the Prefix to "[SOLVED]"
4. Save.

Thanks.

---

