---
title: "keyboard back-light does not dip when monitors goes to sleep"
date: 2013-02-05
forum: General Help
---

### Post by odror on 2013-02-05
Hi

I have a new hp desktop computer with back-light keyboard. When the monitor goes to sleep the keyboard back-light stays on. In fact I do not know how to turn off/on the keyboard back-light.

also:
> $ ls /sys/class/leds
rt2800pci-phy0::assoc  rt2800pci-phy0::quality  rt2800pci-phy0::radio


I do not think that this is keyboard related.

Any help will be appreciated

---

### Post by efflandt on 2013-02-05
What does **lsusb** list the keyboard as (or **sudo lsusb -v** would provide more info)?

Contents of /sys/class/leds is likely related to your network card (mine has ath9k-phy0).

I have a Microsoft Sidewinder X4 keyboard with backlit keys, but rarely boot Windows, so have not paid attention to whether that has any control over keyboard brightness.  A lightbulb key on the keyboard itself can switch between 3 different brightness levels and off. It boots full brightness, but I typically leave it set at medium.

I imagine putting your computer into suspend might turn the keyboard backlight off. But I don't normally do that, because my desktop does not use much power when idle and I seed torrents for Ubuntu, Debian, and Raspbian (Debian wheezy for Raspberry Pi).

---

### Post by odror on 2013-02-05
> **efflandt said:**
> What does **lsusb** list the keyboard as (or **sudo lsusb -v** would provide more info)?


lsusb :> Bus 002 Device 004: ID 04f2:106a Chicony Electronics Co., Ltd 


syslog when plugging the keyboard shows:> Feb  5 17:43:04 XXX kernel: [10362.890338] usb 2-1.6: new low-speed USB device number 5 using ehci_hcd
Feb  5 17:43:04 XXX kernel: [10362.989017] usb 2-1.6: New USB device found, idVendor=04f2, idProduct=106a
Feb  5 17:43:04 XXX kernel: [10362.989022] usb 2-1.6: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Feb  5 17:43:04 XXX kernel: [10362.989025] usb 2-1.6: Product: HP USB Backlit Keyboard
Feb  5 17:43:04 XXX kernel: [10362.989027] usb 2-1.6: Manufacturer: CHICONY
Feb  5 17:43:04 XXX mtp-probe: checking bus 2, device 5: "/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6"
Feb  5 17:43:04 XXX kernel: [10362.992824] input: CHICONY HP USB Backlit Keyboard as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.0/input/input25
Feb  5 17:43:04 XXX kernel: [10362.993129] hid-generic 0003:04F2:106A.0014: input,hidraw4: USB HID v1.11 Keyboard [CHICONY HP USB Backlit Keyboard] on usb-0000:00:1d.0-1.6/input0
Feb  5 17:43:04 XXX mtp-probe: bus: 2, device: 5 was not an MTP device
Feb  5 17:43:04 XXX kernel: [10362.997826] input: CHICONY HP USB Backlit Keyboard as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.1/input/input26
Feb  5 17:43:04 XXX kernel: [10362.997976] hid-generic 0003:04F2:106A.0015: input,hiddev0,hidraw5: USB HID v1.11 Device [CHICONY HP USB Backlit Keyboard] on usb-0000:00:1d.0-1.6/input1

---

