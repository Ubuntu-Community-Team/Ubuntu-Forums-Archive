---
title: "can't return to Xubuntu session after using kvm switch"
date: 2016-01-23
forum: General Help
---

### Post by r.stiltskin on 2016-01-23
I connected an IOGEAR kvm switch to share my keyboard, mouse & monitor between 2 machines.  One running Xubuntu 12.04 works fine.  I can switch away from that machine and return back to it and the GUI session is perfect.  The other, running Xubuntu 14.04 is the problem.  After I switch away to the older box, when I return I have a blank screen and can't find any way to restore it.  The only way to recover is press Ctrl-Alt-F2, login to a tty session and reboot.

It's not a hardware problem, because the same box works fine when I boot it into Windows 7 or Debian Wheezy.  With either of those I can switch back and forth between machines at will.

A possible clue is that when it's running Xubuntu 14.04, immediately after switching back to that box, the monitor goes into "power saving mode".  But in System Settings/Screensaver the Display Power Management is NOT enabled.  Power Manager is set to Never put the computer to sleep, Never put display to sleep, Never switch off display, Never reduce screen brightness, and Light Locker is switched OFF (not enabled).

dmesg output seems about the same on the two machines, but it seems to relate only to the mouse and keyboard.  I don't see anything about the display.  Here's what I get from Debian Wheezy (which works fine):
```

[   51.676535] generic-usb 0003:046D:C064.0002: can't reset device, 0000:00:1d.0-1.6.4/input0, status -71
[   51.680503] usb 6-1.6: clear tt 1 (0050) error -71
[   51.683386] generic-usb 0003:045E:078C.0001: can't reset device, 0000:00:1d.0-1.6.3/input0, status -71
[   51.684761] generic-usb 0003:046D:C064.0002: can't reset device, 0000:00:1d.0-1.6.4/input0, status -71
[   51.687373] usb 6-1.6: clear tt 1 (0040) error -71
[   51.691495] usb 6-1.6: clear tt 1 (0050) error -71
[   51.700503] generic-usb 0003:046D:C064.0002: can't reset device, 0000:00:1d.0-1.6.4/input0, status -71
[   51.704487] usb 6-1.6: clear tt 1 (0050) error -71
[   51.708873] generic-usb 0003:046D:C064.0002: can't reset device, 0000:00:1d.0-1.6.4/input0, status -71
[   51.709607] usb 6-1.6: USB disconnect, device number 3
[   51.709610] usb 6-1.6.3: USB disconnect, device number 4
[   51.712858] usb 6-1.6: clear tt 1 (0050) error -71
[   51.849409] usb 6-1.6.4: USB disconnect, device number 5
[   70.555203] usb 6-1.6: new high-speed USB device number 6 using ehci_hcd
[   70.647634] usb 6-1.6: New USB device found, idVendor=1a40, idProduct=0101
[   70.647640] usb 6-1.6: New USB device strings: Mfr=0, Product=1, SerialNumber=0
[   70.647645] usb 6-1.6: Product: USB 2.0 Hub
[   70.647933] hub 6-1.6:1.0: USB hub found
[   70.648007] hub 6-1.6:1.0: 4 ports detected
[   70.934856] usb 6-1.6.3: new low-speed USB device number 7 using ehci_hcd
[   71.048150] usb 6-1.6.3: New USB device found, idVendor=045e, idProduct=078c
[   71.048156] usb 6-1.6.3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[   71.048160] usb 6-1.6.3: Product: USB Keyboard
[   71.048163] usb 6-1.6.3: Manufacturer: LITEON Technology
[   71.053271] input: LITEON Technology USB Keyboard as /devices/pci0000:00/0000:00:1d.0/usb6/6-1/6-1.6/6-1.6.3/6-1.6.3:1.0/input/input11
[   71.053429] generic-usb 0003:045E:078C.0003: input,hidraw0: USB HID v1.10 Keyboard [LITEON Technology USB Keyboard] on usb-0000:00:1d.0-1.6.3/input0
[   71.138611] usb 6-1.6.4: new low-speed USB device number 8 using ehci_hcd
[   71.252297] usb 6-1.6.4: New USB device found, idVendor=046d, idProduct=c064
[   71.252303] usb 6-1.6.4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[   71.252308] usb 6-1.6.4: Product: USB Optical Mouse
[   71.252311] usb 6-1.6.4: Manufacturer: Logitech
[   71.256977] input: Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb6/6-1/6-1.6/6-1.6.4/6-1.6.4:1.0/input/input12
[   71.257301] generic-usb 0003:046D:C064.0004: input,hidraw1: USB HID v1.10 Mouse [Logitech USB Optical Mouse] on usb-0000:00:1d.0-1.6.4/input0

```

and here's what I get from Xubuntu 14.04 (printed in a TTY window after the GUI session is frozen):
```
[  429.316632] hid-generic 0003:046D:C064.0002: can't reset device, 0000:00:1d.0-1.6.4/input0, status -71
[  429.320612] usb 2-1.6: clear tt 1 (0050) error -71
[  429.331613] hid-generic 0003:045E:078C.0001: can't reset device, 0000:00:1d.0-1.6.3/input0, status -71
[  429.332481] hid-generic 0003:046D:C064.0002: can't reset device, 0000:00:1d.0-1.6.4/input0, status -71
[  429.335618] usb 2-1.6: clear tt 1 (0040) error -71
[  429.339863] usb 2-1.6: clear tt 1 (0050) error -71
[  429.348597] hid-generic 0003:046D:C064.0002: can't reset device, 0000:00:1d.0-1.6.4/input0, status -71
[  429.352591] usb 2-1.6: clear tt 1 (0050) error -71
[  429.363594] hid-generic 0003:045E:078C.0001: can't reset device, 0000:00:1d.0-1.6.3/input0, status -71
[  429.364463] hid-generic 0003:046D:C064.0002: can't reset device, 0000:00:1d.0-1.6.4/input0, status -71
[  429.367598] usb 2-1.6: clear tt 1 (0040) error -71
[  429.371845] usb 2-1.6: clear tt 1 (0050) error -71
[  429.373824] usb 2-1.6: USB disconnect, device number 3
[  429.373827] usb 2-1.6.3: USB disconnect, device number 4
[  429.431014] usb 2-1.6.4: USB disconnect, device number 5
[  434.956324] usb 2-1.6: new high-speed USB device number 6 using ehci-pci
[  435.048877] usb 2-1.6: New USB device found, idVendor=1a40, idProduct=0101
[  435.048883] usb 2-1.6: New USB device strings: Mfr=0, Product=1, SerialNumber=0
[  435.048887] usb 2-1.6: Product: USB 2.0 Hub
[  435.049205] hub 2-1.6:1.0: USB hub found
[  435.049381] hub 2-1.6:1.0: 4 ports detected
[  435.336414] usb 2-1.6.3: new low-speed USB device number 7 using ehci-pci
[  435.450299] usb 2-1.6.3: New USB device found, idVendor=045e, idProduct=078c
[  435.450304] usb 2-1.6.3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  435.450307] usb 2-1.6.3: Product: USB Keyboard
[  435.450309] usb 2-1.6.3: Manufacturer: LITEON Technology
[  435.455336] input: LITEON Technology USB Keyboard as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6.3/2-1.6.3:1.0/input/input18
[  435.455454] hid-generic 0003:045E:078C.0003: input,hidraw0: USB HID v1.10 Keyboard [LITEON Technology USB Keyboard] on usb-0000:00:1d.0-1.6.3/input0
[  435.540463] usb 2-1.6.4: new low-speed USB device number 8 using ehci-pci
[  435.654681] usb 2-1.6.4: New USB device found, idVendor=046d, idProduct=c064
[  435.654686] usb 2-1.6.4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  435.654689] usb 2-1.6.4: Product: USB Optical Mouse
[  435.654691] usb 2-1.6.4: Manufacturer: Logitech
[  435.659809] input: Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6.4/2-1.6.4:1.0/input/input19
[  435.659949] hid-generic 0003:046D:C064.0004: input,hidraw1: USB HID v1.10 Mouse [Logitech USB Optical Mouse] on usb-0000:00:1d.0-1.6.4/input0

```

Any ideas?

Edit: to be precise, the switch is an IOGEAR GCS-922U usb/dvi cable KVM switch.

Edit 2: I just booted the newer machine with a Kubuntu 14.04 live CD and it works fine through switching back and forth between machines.  So the problem seems to be with some setting in my Xubuntu 14.04 installation.

---

### Post by r.stiltskin on 2016-01-24
It seems that this is a bug in xfce.  As mentioned above, it didn't happen when I booted from a Kubuntu 14.04 DVD, and it didn't happen when booted Debian Wheezy Gnome desktop).  It DID happen when I booted from a Linux Mint 17.3 Xfce DVD, and did not happen with Linux Mint 17.3 Cinnamon DVD.

It also did not happen before I was logged into a Xubuntu session -- i.e. if I used the KVM switch to change to the second machine while the lightdm login prompt was showing, I could return to this machine and login.  I'm guessing that xfwm4 is crashing.

My "solution", if that's the right word, was to give up on xfce4 and install cinnamon from tsvetko's ppa here: [https://launchpad.net/~tsvetko.tsvetkov/+archive/ubuntu/cinnamon]("https://launchpad.net/~tsvetko.tsvetkov/+archive/ubuntu/cinnamon").  It looks quite nice and now I can switch back and forth between machines without crashing, so that's good.

I'll mark this thread as solved, even though it can only really be solved by the xfce developers.

---

### Post by r.stiltskin on 2016-01-25
Finally I found a better solution in [UberStudent Forums]("http://uberstudent.com/phpBB/viewtopic.php?f=8&t=633"):
In XFCE System Settings/Session and Startup/Application Autostart checking the box for Gnome Settings Daemon seems to solve this problem.  I checked that box, logged out, logged in again and have tried switching away and back with the KVM switch a few times and so far so good.  The desktop hasn't crashed and no new problems have appeared (yet).

By the way, Cinnamon didn't work out for me.  It looked and felt good at first but it seems that it has no Session Save and Restore capability.  Also, using the mouse wheel to switch desktops (scroll on a blank area of desktop) and using the mouse wheel to raise a window both seem to be unavailable in Cinnamon.  I could probably learn to live without the mouse effects, but lacking Session Save/Restore is a dealbreaker.

---

