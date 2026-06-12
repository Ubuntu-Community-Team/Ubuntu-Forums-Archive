---
title: "Zotac ZBox AQ01 Resume from USB Remote"
date: 2014-06-26
forum: General Help
---

### Post by jingo_man on 2014-06-26
[COLOR=#000000][FONT=Helvetica]I have the Zotac ZBox AQ01 and trying to set it up for use with XBMC.[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]I can get the device to suspend, but not to resume from pressing the power button on the remote.[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]I am using Ubuntu 14.04 and the latest XBMC. I want to try to use the “in kernel” lirc, rather than having to install the separate lirc application, and I am using a modified ir-keytable rc_keymap file.[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]This works for almost everything (some buttons are being recognised, which I hope to fix).[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]I have put in udev rules for all the usb devices, and I have also tried to enable these 1 at a time as well. Neither works.[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]
[/FONT][/COLOR]
```
[COLOR=#000000][FONT=Helvetica]cat /etc/udev/rules.d/90-keyboardwakeup.rules
SUBSYSTEM=="usb", ATTRS{idVendor}=="1d6b", ATTRS{idProduct}=="0001" RUN+="/bin/sh -c 'echo enabled > /sys$env{DEVPATH}/../power/wakeup'"
SUBSYSTEM=="usb", ATTRS{idVendor}=="1d6b", ATTRS{idProduct}=="0002" RUN+="/bin/sh -c 'echo enabled > /sys$env{DEVPATH}/../power/wakeup'"
SUBSYSTEM=="usb", ATTRS{idVendor}=="1d6b", ATTRS{idProduct}=="0003" RUN+="/bin/sh -c 'echo enabled > /sys$env{DEVPATH}/../power/wakeup'"
SUBSYSTEM=="usb", ATTRS{idVendor}=="0bda", ATTRS{idProduct}=="0129" RUN+="/bin/sh -c 'echo enabled > /sys$env{DEVPATH}/../power/wakeup'"
[/FONT][/COLOR]

```[COLOR=#000000][FONT=Helvetica]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]If I enable the 2nd device, resume automatically and immediately follows a suspend action. In all other cases, the remote cannot wake the device. Plugging in a keyboard or mouse does resume.[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]I have the following output from “acpitool -w” as well:[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]
[/FONT][/COLOR]
```
[COLOR=#000000][FONT=Helvetica]sudo acpitool -w
   Device	S-state	  Status   Sysfs node
  ---------------------------------------
  1. RTL	  S4	*enabled   pci:0000:02:00.0
  2. SBAZ	  S4	*disabled  pci:0000:00:14.2
  3. OHC1	  S4	*enabled   pci:0000:00:12.0
  4. EHC1	  S4	*enabled   pci:0000:00:12.2
  5. OHC2	  S4	*enabled   pci:0000:00:13.0
  6. EHC2	  S4	*enabled   pci:0000:00:13.2
  7. OHC3	  S4	*disabled
  8. EHC3	  S4	*disabled
  9. XHC0	  S4	*enabled   pci:0000:00:10.0
  10. ODD8	  S3	*enabled   no-bus:dev2.0
[/FONT][/COLOR]

```[COLOR=#000000][FONT=Helvetica]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]I have also tried forcing the ODD8 device, as it was the only one that listed S3, which I think is suspend, in the /etc/rc.local file with “acpitool -W 10”.[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]
[/FONT][/COLOR]
```
[COLOR=#000000][FONT=Helvetica]sudo lsusb
Bus 002 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 8087:07dc Intel Corp.
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[/FONT][/COLOR]

```[COLOR=#000000][FONT=Helvetica]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]What else can I try? Are there hardware issues with this unit achieving what I want? Do I NEED to use the separate lirc application?[/FONT][/COLOR]

---

### Post by jingo_man on 2014-07-15
bump...

---

