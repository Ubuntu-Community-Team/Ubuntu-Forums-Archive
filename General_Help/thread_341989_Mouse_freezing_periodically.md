---
title: "Mouse freezing periodically"
date: 2007-01-19
forum: General Help
---

### Post by Quite Interesting on 2007-01-19
For the past week or so I've been having a problem with my mouse. Every so often, it can be less than a minute or up to twenty minutes, my mouse stops responding to input only for it to start responding again after a few minutes. As you can imagine this is very annoying.

I seem to have discovered what is happening although what is causing this is totally beyond me. It seems like every so often the computer stop seeing the mouse or the usb driver resets itself. The kern.log file shows this:

```

Jan 19 18:29:53 james-desktop kernel: [17180008.264000] usb 1-1: USB disconnect, address 24
Jan 19 18:29:54 james-desktop kernel: [17180008.568000] usb 1-1: new low speed USB device using ohci_hcd and address 25
Jan 19 18:29:54 james-desktop kernel: [17180008.780000] usb 1-1: configuration #1 chosen from 1 choice
Jan 19 18:29:54 james-desktop kernel: [17180008.796000] input: Logitech USB-PS/2 Optical Mouse as /class/input/input16
Jan 19 18:29:54 james-desktop kernel: [17180008.796000] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:03.0-1

```Every time the mouse stops working a block similar to this one except with all the numbers moved on appears in the kern.log file. I have tried switching the usb port I use but this has no effect. The mouse is a logitech mx510.

Any help in fixing this would be greatly appreciated.

---

