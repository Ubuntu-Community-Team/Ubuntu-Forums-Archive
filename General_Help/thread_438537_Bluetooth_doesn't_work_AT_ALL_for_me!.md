---
title: "Bluetooth doesn't work AT ALL for me!"
date: 2007-05-09
forum: General Help
---

### Post by kwilliam on 2007-05-09
I installed Kubuntu Feisty back when it was Beta, but its completely up to date.  Whenever I try to launch the Bluetooth control module, it freezes (the window becomes unresponsive).  When I run hcitool scan, I get 
```
$ hcitool scan
Scanning ...
Inquiry failed: Connection timed out
$
```

Bluetooth works in Windows Vista, so I know the hardware is OK.  I'm trying to use an ExpressCard Media Remote with my Dell Inspiron 6400 laptop.  The way the bluetooth configuration module "freezes" makes me think that something is severely wrong.  Other people seem to have success with Kubuntu and Bluetooth.  Is there a package that I'm still missing?  Possibly if it is a bug left over from the beta period, should I reinstall bluetooth-related packages?  I've never used Bluetooth before, so any information would be appreciated.

Here's a list of bluetooth related packages on my computer.
```
$ dpkg -l | grep blue
ii  bluetooth                                  3.9-0ubuntu4                           Bluetooth stack utilities
ii  bluez-cups                                 3.9-0ubuntu4                           Bluetooth printer driver for CUPS
ii  bluez-gnome                                0.6-1ubuntu3                           Bluetooth utilities for GNOME
ii  bluez-pin                                  0.30-2.1ubuntu3                        Bluetooth PIN helper with D-BUS support
ii  bluez-utils                                3.9-0ubuntu4                           Bluetooth tools and daemons
ii  gnome-bluetooth                            0.8.0-0ubuntu4                         GNOME Bluetooth tools.
ii  kdebluetooth                               0.99+1.0beta2-1ubuntu5                 KDE Bluetooth Framework
ii  libbluetooth2                              3.9-0ubuntu1                           Library to use the BlueZ Linux Bluetooth sta
```

---

### Post by Ivan Wagner on 2007-05-29
Same problem for me...

I have a Dell Inspiron 640m and my headset is a Logitech HS03 (Mobile traveler headset).

Can anyone of you help us out?

Thanks

---

### Post by beerorkid on 2007-05-29
I use the gnome desktop but use kdebluetooth to transfer pics from my phone.  Not sure if that would help, but might be worth a shot.

---

### Post by kwilliam on 2007-06-15
Good news!  I updated my packages yesterday* with Adept Updater and now bluetooth works!  I am pretty sure none of the updated packages were bluetooth related, but there was a kernel update, which may have been what fixed it.

*I had been putting off updating until I had time to make a full backup, because kernel updates sometimes break things.

**[COLOR="Red"]Edit: This is what I had to do for Kubuntu Feisty 7.04.[/COLOR]  In Gutsy 7.10, it appears the KBluetooth system tray applet handles connecting automatically for Kubuntu users.  Just press a button on the remote, and a dialog appears asking if you want to use it as an input device.  Just click "always allow" and it works like magic.  I assume Gnome does something similar.  The key-mapping bit may still be required.**

Anyway, here's how it went.
```
$ hcitool scan
Scanning ...
        00:15:D8:00:60:D9       Interlink VP6600 Media Remote Control
$ sudo hidd --connect 00:15:D8:00:60:D9
```

Damn easy. Fifteen out of 17 keys worked with no extra configuration.  Only the Fast Forward and Rewind buttons had to be mapped
```
# For Interlink Media Remote
xmodmap -e "keycode 152 = XF86Back"
xmodmap -e "keycode 180 = XF86Forward"
```
(Technically, I think XF86Back and Forward are for web browsing, but I don't know if there are Rewind and FastForward buttons.)

However, my keybindings were a little messed up to start with since I installed during Beta, so maybe other's won't even have to do that.  (Also note that the keycodes might be different on different computers.  Mine is a Dell Inspiron 6400.)

[COLOR="#ff0000"]Updated:[/COLOR]

Lastly, I used added a launcher to run "sudo hidd --connect 00:15:D8:00:60:D" so I could connect with one click.  "hidd" still required root priviledges however, so I ran:
```
$ visudo
```
and added the line
```
kwilliam ALL = NOPASSWD: /usr/bin/hidd
```
Obviously, replace "kwilliam" with your login name.

---

