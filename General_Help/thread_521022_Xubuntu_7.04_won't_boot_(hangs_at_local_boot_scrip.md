---
title: "Xubuntu 7.04 won't boot (hangs at local boot scripts)"
date: 2007-08-08
forum: General Help
---

### Post by alan_daniel on 2007-08-08
I've got Xubuntu 7.04 installed on a 5 or 6-year-old Thinkpad R31 with 384 megs RAM. I've been using linux back since the days of Mandrake 9.0 (2002) and made the full switch to (x)(k)ubuntu with 5.04. This laptop, like many of its time period, does not have wireless internet capabilities, and therefore, I have had to use a linksys WPC54GS pci card. I've had varied success with it over the years (I like to reinstall and try new things), and it's been almost 50% "it just works."

I just tried the other day to see if it would "just work," and although it picked up wireless capabilities, I couldn't connect to anything. Frustrated, I turned off the computer and tried again today, only to find that it would not boot. The boot process starts normally then heads to a standard tty and leaves me with this on the screen (it's a tty, so I don't know of a way to scroll up and see what's written above).

```
/etc/rc2.d/S20hotkey-setup: line 116: /usr/share/hotkey-setup/default.hk: Not a directory
/etc/rc2.d/S20hotkey-setup: line 118: /usr/share/hotkey-setup/generic.hk: Not a directory
/etc/rc2.d/S20nvidia-kernel: 40: seq: not found
/etc/rc2.d/S98usplash: 82: clear: not found
/etc/rc2.d/S99acpi-support: line 7: /usr/share/acpi-support/power-funcs: Not a directory
 * Checking battery state...
/etc/acpi/start.d/10-save-dmidecode.sh: line 9: dmidecode: command not found
/etc/acpi/start.d/10-save-dmidecode.sh: line 10: dmidecode: command not found
/etc/acpi/start.d/10-save-dmidecode.sh: line 11: dmidecode: command not found
/etc/acpi/start.d/10-save-dmidecode.sh: line 12: dmidecode: command not found
/etc/acpi/start.d/60-asus-wireless-led.sh: line 2: /usr/share/acpi-support/state-funcs: Not a directory
/etc/acpi/start.d/60-asus-wireless-led.sh: line 3: isAnyWirelessPoweredOn: command not found
/etc/acpi/start.d/60-asus-wireless-led.sh: line 6: setLEDAsusWireless: command not found
   ...done.
 * Running local boot scripts (/etc/rc.local)
   ...done.
```

I need to make it clear that it does not give me a login shell, even if I press enter. It just hangs there with the only solution being a hard reboot.

Also, concerning the acpi, this laptop has a known BIOS bug that prevents acpi/apm usage without a mouse spasm, but I am almost certain I had acpi deactivated.

Sorry this was such a long post/question, I am just stuck. Any help is greatly appreciated.

---

