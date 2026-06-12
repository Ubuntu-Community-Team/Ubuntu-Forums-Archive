---
title: "Interpret dmesg log"
date: 2014-08-09
forum: General Help
---

### Post by em3raldxiii on 2014-08-09
It's very simple:  There are various points during a boot-up & log-in to my Ubuntu machine where I am experiencing dramatic slow downs.  I normally don't stress because my computer is *rarely *turned off, but I finally decided to do some investigating.

One such instance is noted here in my dmesg log:

11.749917] usb 7-2: new full-speed USB device number 3 using ohci-pci
[   11.923225] usb 7-2: New USB device found, idVendor=06a3, idProduct=8014
[   11.923233] usb 7-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[   11.923239] usb 7-2: Product: Eclipse Litetouch Keyboard
[   11.923243] usb 7-2: Manufacturer: Saitek
[   11.929492] input: Saitek Eclipse Litetouch Keyboard as /devices/pci0000:00/0000:00:16.0/usb7/7-2/7-2:1.0/input/input5
[   11.929623] hid-generic 0003:06A3:8014.0007: input,hidraw0: USB HID v1.11 Keyboard [Saitek Eclipse Litetouch Keyboard] on usb-0000:00:16.0-2/input0
[   11.936386] input: Saitek Eclipse Litetouch Keyboard as /devices/pci0000:00/0000:00:16.0/usb7/7-2/7-2:1.1/input/input6
[   11.936587] hid-generic 0003:06A3:8014.0008: input,hiddev0,hidraw1: USB HID v1.11 Device [Saitek Eclipse Litetouch Keyboard] on usb-0000:00:16.0-2/input1
[   36.164096] Adding 19535036k swap on /dev/sda3.  Priority:-1 extents:1 across:19535036k FS
[   36.231090] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   36.323936] systemd-udevd[372]: starting version 204
[   36.454271] lp: driver loaded but no devices found

As you can see, there is a 24 second break between something about my USB Saitek keyboard and then adding the swap.  I am mostly just looking for confirmation that I am interpreting this right:  Is this telling me that my keyboard is causing this peculiar 24 second wait period?

I could probably grab a stopwatch and time the login sequence while a different keyboard is installed ... but I don't have one handy, and I don't want to buy a new keyboard unless I know this is the culprit.  Besides, I **love** this keyboard!

So, as always, I am very receptive to any sort of suggestion ... even just theories.  I need somewhere to start, and I figure if I can cut down the wait time by 24 seconds in one shot, I'd be making good headway.

Bonus Question:
What stage is this delay occuring in?  Is this during initial startup (prior to seeing the log-in screen), is it a delay on the log-in screen (there is always a significant wait before I can select a user to log into), or is it during the log-in stage (once I have entered my password and wait for my desktop to show up)?

---

### Post by tgalati4 on 2014-08-10
Will the computer boot up without the keyboard?  How much time does it take?  That would give you an indication of the boot time difference.  It's possible that the module needed to activate the keyboard is interfering with the bootup process.  Check your BIOS settings turn on or off "Support Legacy USB devices" and "Allow USB devices to Wake".

Try another, generic USB keyboard and note the boot differences.

You can install *bootchart* to get into the details:

> 
tgalati4@Mint14-Extensa ~ $ apt-cache search bootchart
bootchart - boot sequence auditing
pybootchartgui - boot sequence visualisation


---

### Post by em3raldxiii on 2014-08-11
@tgalati4:  I haven't tried rebooting with the keyboard disconnected, I think I have to change a setting in the BIOS to let it do so without halting.  I don't have a generic keyboard at hand, but that was my next guess too.  As for the legacy support and so-on, I also briefly thought of that, but I discounted it (possibly in error) because I couldn't figure out why that would cause such a delay.  Finally, thanks for those bootchart apps; I will _definitely_ give them a go.

---

### Post by tgalati4 on 2014-08-11
Change the setting in BIOS "Halt on Errors" to "Halt on Errors, except keyboard"  or "Ignore Errors" or something to that effect.

---

### Post by em3raldxiii on 2014-08-11
Yep, next time I am at home with a little time to play around, I'll do that.

---

