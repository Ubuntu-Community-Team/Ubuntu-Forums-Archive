---
title: "Ubuntu 23.10, Steam and Xbox Elite Wireless Controller Series 2"
date: 2024-02-10
forum: General Help
---

### Post by uipojehdx on 2024-02-10
Hi there - I am using Ubuntu 23.10 and I have installed steam via the Ubuntu default repository (sudo apt install steam-installer steam-devices). Steam is working fine, I can download games etc. I can connect my Xbox Elite Wireless Controller Series 2 via bluetooth and ubuntu recognises it, however steam does not. When I physically plug the controller into computer, steam then does recognise the controller, but it has to stay plugged in.

Does anyone know how I can connect the controller wirelessly and have steam recognise it?

Thank you for reading!

---

### Post by mrkuser on 2024-03-17
Hello

I get the exact same problem with Kubuntu 23.10, same controller.

I've been doing some investigation, managed to get it working properly on a Debian system.

Working Debian System:

journalctl -fx
Mar 17 21:49:45 silver kernel: input: Xbox Wireless Controller as [I]/devices/virtual/misc/uhid/0005:045E:0B22.0002/input/input15
Mar 17 21:49:45 silver kernel: input: Xbox Wireless Controller Keyboard as /devices/virtual/misc/uhid/0005:045E:0B22.0002/input/input16
Mar 17 21:49:45 silver kernel: hid-generic 0005:045E:0B22.0002: input,hidraw0: BLUETOOTH HID v5.13 Gamepad [Xbox Wireless Controller] on 50:b7:c3:f1:62:8b

Not working Kubuntu system:
[COLOR=#000000]Mar 17 22:33:23 GS65-Stealth-9SF kernel: input: Xbox Wireless Controller as /devices/virtual/misc/uhid/0005:045E:0B22.0041/input/input92
[/COLOR]Mar 17 22:33:23 GS65-Stealth-9SF kernel: microsoft 0005:045E:0B22.0041: input,hidraw10: BLUETOOTH HID v5.13 Gamepad [Xbox Wireless Controller] on a0:51:0b:46:c1:f1

Could the extra input device on the Debian system be part of the problem?
Also noticed it shows as hid-generic on the working system and microsoft on the one that doesn't work.[/I]

---

