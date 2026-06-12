---
title: "USB Keyboard Unresponsive"
date: 2008-01-22
forum: General Help
---

### Post by chazco on 2008-01-22
Hi,

I have a USB keyboard which doesn't always work at boot time (although sometimes it will work fine), despite dmesg indicating that Ubuntu has detected it. Moving the keyboard to a different USB port fixes the issue (it doesn't matter which port it starts from).

Relevant dmesg output:
```

[   28.255293] input: Microsoft Comfort Curve Keyboard 2000 as /class/input/input2
[   28.255305] input: USB HID v1.11 Keyboard [Microsoft Comfort Curve Keyboard 2000] on usb-0000:00:02.0-4
[   28.272233] input: Microsoft Comfort Curve Keyboard 2000 as /class/input/input3
[   28.272247] input: USB HID v1.11 Device [Microsoft Comfort Curve Keyboard 2000] on usb-0000:00:02.0-4

... Keyboard unresponsive, so move to another port...

[  181.012000] input: Microsoft Comfort Curve Keyboard 2000 as /class/input/input8
[  181.012000] input: USB HID v1.11 Keyboard [Microsoft Comfort Curve Keyboard 2000] on usb-0000:01:05.0-2
[  181.028000] input: Microsoft Comfort Curve Keyboard 2000 as /class/input/input9
[  181.028000] input: USB HID v1.11 Device [Microsoft Comfort Curve Keyboard 2000] on usb-0000:01:05.0-2

```

Modifying the BIOS options for USB keyboard support doesn't have any effect. If the keyboard is connected to the motherboard then the BIOS and GRUB menu both work fine. If I use a PS2->USB adapter even the BIOS fails to detect the keyboard.

Any ideas on fixing this permanently?

---

### Post by dominikroblek on 2008-02-02
Have you enabled UDB keyboard support your BIOS?

---

