---
title: "My new wacom intuos tablet won't work"
date: 2018-09-21
forum: General Help
---

### Post by anjubatus on 2018-09-21
First, I'm not very good at using the terminal yet, I've installed some packages with it and that's it. So if you have any instructions to me please give me the whole text to type in? It's just that I've seen in some places ppl just say to 'run x with y' or similar and i could no longer follow. But anyway...

I very recently bought a wacom intuos tablet and pen, completely new. When I put the usb in (in my chromebook with ubuntu), the white light on the tablet lights up, but the stylus won't move anywhere.
Typing in lsusb prints out this:
```
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 8087:07dc Intel Corp. 
Bus 001 Device 010: ID 0bda:57cf Realtek Semiconductor Corp. 
Bus 001 Device 011: ID 056a:0374 Wacom Co., Ltd 
Bus 001 Device 002: ID 05e3:0610 Genesys Logic, Inc. 4-port hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
``` I also found this command ('sudo dmesg | grep -i wacom') and this is what it prints out, if it tells you anything:

```
[COLOR=#000000][   69.883961] usb 1-2.1: Manufacturer: Wacom Co.,Ltd.[/COLOR][   69.903168] input: Wacom Co.,Ltd. Intuos S Pen as /devices/pci0000:00/0000:00:14.0/usb1/1-2/1-2.1/1-2.1:1.0/0003:056A:0374.0001/input/input9
[   69.904268] wacom 0003:056A:0374.0001: hidraw0: USB HID v1.10 Device [Wacom Co.,Ltd. Intuos S] on usb-0000:00:14.0-2.1/input0
[ 1730.556742] wacom 0003:056A:0374.0001: wacom_set_report: ran out of retries (last error = -32)
[ 6290.376424] wacom 0003:056A:0374.0001: wacom_set_report: ran out of retries (last error = -32)
[11396.777097] wacom 0003:056A:0374.0001: wacom_set_report: ran out of retries (last error = -32)
[11701.623393] wacom 0003:056A:0374.0001: wacom_set_report: ran out of retries (last error = -32) 
[27591.742891] wacom 0003:056A:0374.0001: wacom_set_report: ran out of retries (last error = -32)
```
Could someone help me figure this out, or at least tell me where to get help?

---

