---
title: "Purple tinted monitor and resolution limited to 1024x768"
date: 2012-12-17
forum: General Help
---

### Post by jclmusic on 2012-12-17
Hi all,
I have no idea what happened, but I think it may be due to drivers updating automatically? (I didn't ask them to!)

Anyway, as of yesterday Ubuntu will only allow me to have a maximum screen resolution of 1024x768 and everything has a purple hue/tint. 

I've tried re-installing and am still having the same problem. It's as if my monitor is no longer recognised? New driver versions? It was working fine for months up until yesterday. 

Any ideas?

---

### Post by Pjotr123 on 2012-12-17
Post a hardware list like this:
[https://sites.google.com/site/easylinuxtipsproject/tips#TOC-Make-automatically-a-nice-document-with-all-your-hardware-information](https://sites.google.com/site/easylinuxtipsproject/tips#TOC-Make-automatically-a-nice-document-with-all-your-hardware-information)

---

### Post by jclmusic on 2012-12-17
> **Pjotr123 said:**
> Post a hardware list like this:
[https://sites.google.com/site/easylinuxtipsproject/tips#TOC-Make-automatically-a-nice-document-with-all-your-hardware-information](https://sites.google.com/site/easylinuxtipsproject/tips#TOC-Make-automatically-a-nice-document-with-all-your-hardware-information)

Attached...

---

### Post by Pjotr123 on 2012-12-17
You have an Nvidia GeForce 8400 GS video card. Is it running on the restricted driver (which it should)?

Check it like this:
[https://sites.google.com/site/easylinuxtipsproject/first#TOC-Make-sure-all-hardware-is-working-properly-and-install-missing-drivers](https://sites.google.com/site/easylinuxtipsproject/first#TOC-Make-sure-all-hardware-is-working-properly-and-install-missing-drivers)

---

### Post by jclmusic on 2012-12-17
> **Pjotr123 said:**
> You have an Nvidia GeForce 8400 GS video card. Is it running on the restricted driver (which it should)?

Check it like this:
[https://sites.google.com/site/easylinuxtipsproject/first#TOC-Make-sure-all-hardware-is-working-properly-and-install-missing-drivers](https://sites.google.com/site/easylinuxtipsproject/first#TOC-Make-sure-all-hardware-is-working-properly-and-install-missing-drivers)

It is as far as I'm aware. The 'Additional Drivers' program fails to load though. Is there a terminal code I can run to check which drivers are being used?

Trying to run the program from Terminal gives this error:
```

dusepo@dusepo-desktop:~$ sudo jockey-gtk

(jockey-gtk:2927): Gtk-CRITICAL **: gtk_icon_set_render_icon_pixbuf: assertion `icon_set != NULL' failed

(jockey-gtk:2927): Gtk-CRITICAL **: gtk_icon_set_render_icon_pixbuf: assertion `icon_set != NULL' failed
Traceback (most recent call last):
  File "/usr/bin/jockey-gtk", line 418, in <module>
    sys.exit(u.run())
  File "/usr/lib/python2.7/dist-packages/jockey/ui.py", line 468, in run
    self.ui_show_main()
  File "/usr/bin/jockey-gtk", line 94, in ui_show_main
    self.update_tree_model()
  File "/usr/bin/jockey-gtk", line 275, in update_tree_model
    info = self.get_ui_driver_info(h_id)
  File "/usr/lib/python2.7/dist-packages/jockey/ui.py", line 295, in get_ui_driver_info
    info = self.backend().handler_info(handler_id)
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 145, in __call__
    **keywords)
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Python.ValueError: Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/dbus/service.py", line 707, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/python2.7/dist-packages/jockey/backend.py", line 264, in handler_info
    'recommended': str(h.recommended()),
  File "/usr/share/jockey/handlers/nvidia.py", line 130, in recommended
    nd = NvidiaDetection()
  File "/usr/lib/python2.7/dist-packages/NvidiaDetector/nvidiadetector.py", line 68, in __init__
    self.getData()
  File "/usr/lib/python2.7/dist-packages/NvidiaDetector/nvidiadetector.py", line 149, in getData
    driver_version = self.__get_value_from_name(stripped_package_name)
  File "/usr/lib/python2.7/dist-packages/NvidiaDetector/nvidiadetector.py", line 87, in __get_value_from_name
    v = int(name)
ValueError: invalid literal for int() with base 10: 'experimental-304'

```

---

### Post by Pjotr123 on 2012-12-17
Try this:
```
sudo apt-get install nvidia-current
```

After the installation: reboot your machine.

---

### Post by Grenage on 2012-12-17
> **jclmusic said:**
> Hi all,
I have no idea what happened, but I think it may be due to drivers updating automatically? (I didn't ask them to!)

Anyway, as of yesterday Ubuntu will only allow me to have a maximum screen resolution of 1024x768 and everything has a purple hue/tint. 

I've tried re-installing and am still having the same problem. It's as if my monitor is no longer recognised? New driver versions? It was working fine for months up until yesterday. 

Any ideas?

Got a spare monitor cable?

---

### Post by jclmusic on 2012-12-17
> **Pjotr123 said:**
> Try this:
```
sudo apt-get install nvidia-current
```

After the installation: reboot your machine.

Looks like it's already installed, so must be using that driver?

```

dusepo@dusepo-desktop:~$ sudo apt-get install nvidia-current
Reading package lists... Done
Building dependency tree       
Reading state information... Done
nvidia-current is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 268 not upgraded.

```

> **Grenage said:**
> Got a spare monitor cable?

I tried another VGA cable earlier and it's the same. My graphics card has a digital plug on it but sadly my monitor doesn't.

---

### Post by Grenage on 2012-12-17
Are you able to try another monitor?  Is the coloured hue present during the BIOS screen, or only after drivers have loaded?

---

### Post by Pjotr123 on 2012-12-17
Try to configure your monitor like this:
```
gksudo nvidia-settings
```

Start with the X Server Display Configuration - tab Display - Resolution - *change it* - Save to X Configuration File 

Close and reboot.

---

### Post by jclmusic on 2012-12-17
> **Grenage said:**
> Are you able to try another monitor?  Is the coloured hue present during the BIOS screen, or only after drivers have loaded?

The hue is present at BIOS screen too. The text which should be white is now a light purple. I know this might suggest the monitor has gone bad, but why the sudden resolution limitations?

> **Pjotr123 said:**
> Try to configure your monitor like this:
```
gksudo nvidia-settings
```

Start with the X Server Display Configuration - tab Display - Resolution - *change it* - Save to X Configuration File 

Close and reboot.

I clicked 'X Server Display Configuration' but can't see a 'Display' tab? I've attached a screenshot of the window. I should add that it seems to think my monitor is a CRT, but it's actually a TFT flatscreen.

---

### Post by Grenage on 2012-12-17
> **jclmusic said:**
> The hue is present at BIOS screen too. The text which should be white is now a light purple. I know this might suggest the monitor has gone bad, but why the sudden resolution limitations?

You're looking at a broken monitor, or a damaged cable/port; you've ruled out the cable.

The bad res is down to damaged/destroyed EDID data, which is what the machine uses to get acceptable resolutions.  Linux machines are particularly reliant on it, although you can usually get around it with a modeline in xorg.conf.  EDID data often fails to get through due to a bad connection.

So unless you can live with the hue, I'd start wiggling those ports - you might get lucky.

---

### Post by jclmusic on 2012-12-17
> **Grenage said:**
> You're looking at a broken monitor, or a damaged cable/port; you've ruled out the cable.

The bad res is down to damaged/destroyed EDID data, which is what the machine uses to get acceptable resolutions.  Linux machines are particularly reliant on it, although you can usually get around it with a modeline in xorg.conf.  EDID data often fails to get through due to a bad connection.

So unless you can live with the hue, I'd start wiggling those ports - you might get lucky.

Wiggling both ends has no effect. So it is in fact a bad monitor? It's under a year old! :(

---

### Post by Grenage on 2012-12-17
> **jclmusic said:**
> So it is in fact a bad monitor? It's under a year old! :(

That's good; it's probably still covered by the warranty.  If you can, plug it into another machine - just to be sure.  It could be the GFX port on the PC, but it's less likely.

I'm off for the evening, but am sure others will post here if you have any further questions. :)

---

### Post by jclmusic on 2012-12-17
> **Grenage said:**
> That's good; it's probably still covered by the warranty.  If you can, plug it into another machine - just to be sure.  It could be the GFX port on the PC, but it's less likely.

I'm off for the evening, but am sure others will post here if you have any further questions. :)

Thanks for your help. Have a good evening!

---

