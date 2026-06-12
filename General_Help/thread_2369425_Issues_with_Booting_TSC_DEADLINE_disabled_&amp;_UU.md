---
title: "Issues with Booting: TSC_DEADLINE disabled &amp; UUID not found"
date: 2017-08-22
forum: General Help
---

### Post by lufredlow on 2017-08-22
I am having problems booting my Ubuntu after an attempted hardware fix today. My laptop was working fine but had some *minor* issues, so we tried a different motherboard, which had a major issue, so we changed it back to the original board. However, now I have problem booting.

I seem to have two issues, which may or may not be related (I am very lost).

When I try to boot to my normal day-to-day Ubuntu, I get an error message saying:
```
[COLOR=#111111][FONT=Consolas]
[/FONT][/COLOR][    0:000000] [Firmware Bug]: TSC_DEADLINE disabled due to Errata; please update microcode to version: 0x52 (or later)[COLOR=#111111][FONT=Consolas]
[/FONT][/COLOR]
```
and get stuck at initramfs.

When I try to boot into recovery mode, I get:
```

Gave up waiting for root device. Common problems:
  - Boot args (Cat /proc/cmdline)
    - Check rootdelay= (did the system wait long enough?)
    - Check root= (did the system wait for the right device?)
  - Missing modules (cat /proc/modules; ls /dev)
ALERT! UUID=xxxxxxxxxxxxxxxxxxxxxx does not exist. Dropping to a shell!
[    50.177360] usbcore: registered with new interface driver usbhid
[    50.177845] usbhid: USB HID core driver

```
and get stuck at BusyBox initramfs again.

I don't know if the two issues are related, but either way, I cannot boot into my Ubuntu properly. :(

---

### Post by oldfred on 2017-08-23
what brand/model system? SSD?
UEFI or BIOS?
Have you tried updating firmware?

Deadline is one of the default schedulers one in [] is current one.
  cat /sys/block/sda/queue/scheduler
noop [deadline] cfq 

Many with Dell have had to update UEFI and firmware on SSD.

In my Asus UEFI system, synaptic search shows I have about 12 apps with firmware in description installed.

---

