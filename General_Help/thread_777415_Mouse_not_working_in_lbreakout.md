---
title: "Mouse not working in lbreakout"
date: 2008-05-01
forum: General Help
---

### Post by ripper17 on 2008-05-01
Hi all
I've got a pretty strange problem at my fathers computer: He has an IBM Thinkpad with Kubuntu. I think it's still a dated 6.10 because I don't get round doing an update and he's using it quite a lot, so I cannot leave it "not working" for a couple of days.
Anyway, the laptop is in its docking station, and attached to it is a Genius XSCROLL mouse, which works fine in almost all circumstances but one: Playing lbreakout. I can even use the mouse in the lbreakout menu - but not in the game itself.
dmesg gives me:
```
[17179595.316000] input: USB HID v1.10 Mouse [Genius NetScroll + Traveler] on usb-0000:00:1d.7-4.1
```
lsmod:
```
usbcore               134912  4 usbhid,ehci_hcd,uhci_hcd
psmouse                41352  0
```

and /dev/input/mice exists (which was pointed out in another thread as a possible error source)

Do I need to modify the xorg.conf file? 
xorg.conf holds:
```
Section "InputDevice"
  Identifier  "Configured Mouse"
  Driver      "mouse"
  Option      "CorePointer"
  Option      "Device" "/dev/input/mice"
  Option      "Protocol" "ExplorerPS/2"
  Option      "ZAxisMapping" "4 5"
  Option      "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
  Identifier  "Synaptics Touchpad"
  Driver      "synaptics"
  Option      "SendCoreEvents" "true"
  Option      "Device" "/dev/psaux"
  Option      "Protocol" "auto-dev"
  Option      "SHMConfig" "on"
  Option      "HorizScrollDelta" "0"
EndSection

```

If you need any more information, I'll be glad to supply it (though maybe not too quickly, since I'm not always at my fathers computer)

Martin

---

