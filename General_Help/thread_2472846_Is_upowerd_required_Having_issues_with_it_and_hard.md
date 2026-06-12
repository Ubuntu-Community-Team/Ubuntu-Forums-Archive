---
title: "Is upowerd required? Having issues with it and hard drives"
date: 2022-03-14
forum: General Help
---

### Post by sfatula on 2022-03-14
So, here's what is happening. ubuntu 20.04.4, 5.13.0-35-generic kernel. This is a non laptop machine. Every so often, generally within a day after reboot and never again, my syslog gets a ton of messages in a row such as:

Mar 14 09:59:17 Home-Server upowerd[7195]: treating change event as add on /sys/devices/pci0000:00/0000:00:14.0/usb1
Mar 14 09:59:17 Home-Server upowerd[7195]: treating change event as add on /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.2/usb3
Mar 14 09:59:17 Home-Server upowerd[7195]: treating change event as add on /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.2/usb4

There were 153 of these upowerd messages today all in a row today. Right after these, I then get a message such as:

Mar 14 10:00:55 Home-Server kernel: [376348.449655]  sdb: sdb1 sdb9

And that appears to then trigger zfs to think it's needs to do a resilver for sdb. Which I guess would be because it thinks the drive went offline. It's a random drive, always exactly one, and always only right after upowerd fires. I want to avoid all that of course. Happens every time, within a day of rebooting and never again until after next reboot strangely. Can't seem to figure out what starts the chain and why upowerd seems to start it.

The last 2 times, I've seen this right after systemd reloading which was livepatch it appears. So, maybe systemd reloading triggering upowerd? Why would upowerd be changing all these devices states and causing the drive re-discover or whatever that message is. Random drive, always exactly 1. Controller is a sas2116_1, i.e. a LSI 9201-16e

Any thoughts to mitigate this?

---

### Post by #&amp;thj^% on 2022-03-14
> **sfatula said:**
> 

The last 2 times, I've seen this right after systemd reloading which was livepatch it appears. So, maybe systemd reloading triggering upowerd? Why would upowerd be changing all these devices states and causing the drive re-discover or whatever that message is. Random drive, always exactly 1. Controller is a sas2116_1, i.e. a LSI 9201-16e

Any thoughts to mitigate this?

Upower= Abstraction for enumerating power devices, listening to device events and querying history and statistics

Hard to guess with only what you show here, try monitoring it for a bit with:
```
upower --monitor-detail

```
if anything useful shows then paste back here to see. wrapped in code tags please. 
Now as far as naming goes EXAMPLE ONLY:
```
[15:07:52.033]	device changed:     /org/freedesktop/UPower/devices/battery_BAT0
  native-path:          BAT0
  vendor:               Celxpert
  model:                L19C4PC0
  serial:               1532
  power supply:         yes
  updated:              Mon 14 Mar 2022 03:07:52 PM MDT (0 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:             yes
    rechargeable:        yes
    state:               fully-charged
    warning-level:       none
    energy:              55.43 Wh
    energy-empty:        0 Wh
    energy-full:         58.34 Wh
    energy-full-design:  60 Wh
    energy-rate:         0 W
    voltage:             17.062 V
    charge-cycles:       9
    percentage:          95%
    capacity:            97.2333%
    technology:          lithium-polymer
    icon-name:          'battery-full-charged-symbolic'

[15:07:52.888]	device changed:     /org/freedesktop/UPower/devices/mouse_hidpp_battery_0
  native-path:          hidpp_battery_0
  model:                Marathon Mouse/Performance Plus M705
  serial:               406d-4f-17-60-0b
  power supply:         no
  updated:              Mon 14 Mar 2022 03:07:52 PM MDT (0 seconds ago)
  has history:          yes
  has statistics:       yes
  mouse
    present:             yes
    rechargeable:        yes
    state:               discharging
    warning-level:       none
    battery-level:       normal
    percentage:          55% (should be ignored)
    icon-name:          'battery-low-symbolic'

``` 
This might be related to networking.
Forgot to add to stop monitoring use keys Ctrl + c

---

### Post by sfatula on 2022-03-14
If you want more logs, see attached log. Everything before and after this section is "normal" logging. 

I can do the monitor-detail though nothing will ever show, until next reboot due to software updates. But it's not a problem. The key will be to remember to do so starting after next software update requiring next reboot!

---

### Post by #&amp;thj^% on 2022-03-14
> **sfatula said:**
>  The key will be to remember to do so starting after next software update requiring next reboot!

I should of said that, good catch.
From the readings I see from your log, at first glance>> it is to do with Networking.
EG: 
```
Home-Server upowerd[7195]: treating change event as add on /sys/devices/pci0000:00/0000:00:14.0/usb1/1-11/1-11:1.0
``` 
Has at least a half dozen entries, is this a WiFi Dongle?

---

### Post by #&amp;thj^% on 2022-03-14
BTW, you can just remove upower, I'm "not" saying it's recommended, but you can, hell it is a Dekstop PC after all.
You can uninstall or remove an installed upower package itself from Ubuntu. 

```
sudo apt remove upower
``` 

If you would like to remove upower and it's dependent packages which are no longer needed from Ubuntu,

```
sudo apt remove --auto-remove upower
``` 

If you use purge options to upower package all the configuration and dependent packages will be removed.

```
sudo apt purge upower
``` 

If you use purge options along with auto remove, All will be removed everything regarding the package, It's really useful when you want to reinstall again.

```
sudo apt purge --auto-remove upower
```

---

### Post by sfatula on 2022-03-14
> **1fallen said:**
> I should of said that, good catch.

Has at least a half dozen entries, is this a WiFi Dongle?

That is a Valve steam controller. 

```
[    2.423693] usb 1-11: new high-speed USB device number 5 using xhci_hcd
[    2.573051] usb 1-11: New USB device found, idVendor=05e3, idProduct=0608, bcdDevice=85.36
[    2.573063] usb 1-11: New USB device strings: Mfr=0, Product=1, SerialNumber=0
[    2.573069] usb 1-11: Product: USB2.0 Hub
[    2.574140] hub 1-11:1.0: USB hub found
[    2.574444] hub 1-11:1.0: 4 ports detected
[    3.107690] usb 1-11.2: new full-speed USB device number 8 using xhci_hcd
[    3.212002] usb 1-11.2: New USB device found, idVendor=28de, idProduct=1142, bcdDevice= 0.01
[    3.212014] usb 1-11.2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    3.212020] usb 1-11.2: Product: Steam Controller
[    3.212024] usb 1-11.2: Manufacturer: Valve Software
[    3.925617] input: Valve Software Steam Controller Keyboard as /devices/pci0000:00/0000:00:14.0/usb1/1-11/1-11.2/1-11.2:1.0/0003:28DE:1142.0005/input/input8
[    3.983975] input: Valve Software Steam Controller Mouse as /devices/pci0000:00/0000:00:14.0/usb1/1-11/1-11.2/1-11.2:1.0/0003:28DE:1142.0005/input/input9
[    4.088471] input: Valve Software Steam Controller as /devices/pci0000:00/0000:00:14.0/usb1/1-11/1-11.2/1-11.2:1.0/0003:28DE:1142.0005/input/input10

```

---

### Post by #&amp;thj^% on 2022-03-14
Aha Ok!
Anyway up to you on the removal of upower.

---

### Post by sfatula on 2022-03-15
[QUOTE=1fallen;14085890]BTW, you can just remove upower, I'm "not" saying it's recommended, but you can, hell it is a Dekstop PC after all.
You can uninstall or remove an installed upower package itself from Ubuntu. 

```
sudo apt remove upower
``` 

You actually can't do that on desktop as you will end up uninstalling gdm3 amongst other rather important things. Better to stop then mask it.

---

### Post by #&amp;thj^% on 2022-03-15
> **sfatula said:**
> [QUOTE=1fallen;14085890]BTW, you can just remove upower, I'm "not" saying it's recommended, but you can, hell it is a Dekstop PC after all.
You can uninstall or remove an installed upower package itself from Ubuntu.[/quote 

```
sudo apt remove upower
``` 

You actually can't do that on desktop as you will end up uninstalling gdm3 amongst other rather important things. Better to stop then mask it.
Good info, I don't use Gnome or GDM3.

---

