---
title: "new build graphics optimization?"
date: 2020-02-25
forum: General Help
---

### Post by maclenin on 2020-02-25
I have built a desktop:
```
Motherboard: Gigabyte Z390 M
CPU: Intel(R) Core(TM) i5-9600K CPU @ 3.70GHz
Graphics: Intel UHD Graphics 630
Display: Samsung TV (old, though HD compatible) connected via HDMI
OS: xubuntu 18.04.4
```
Essentially, all seems to be working beautifully, but for the graphics.

Images and video seem clear, smooth and hi-res.

However, the rendering of fonts and other graphical elements, logos, spreadsheets, menus - is grainy / low res / pixelated - and, certainly, not what I'd expect from this latest generation of hardware.

The display resolution is set to 1920 x 1080 @ 60hz and connected via HDMI (at both ends).

I have also fiddled with the rendering / anti-aliasing appearance settings - without success.

HDMI audio seems to work well.

Here are few other details - via the command line:
```
$ inxi -Gxx
Graphics:
Card: Intel Device 3e98 bus-ID: 00:02.0 chip-ID: 8086:3e98
Display Server: x11 (X.Org 1.19.6 )
drivers: modesetting (unloaded: fbdev,vesa)
Resolution: 1920x1080@60.00hz
OpenGL: renderer: Mesa DRI Intel UHD Graphics 630 (Coffeelake 3x8 GT2)
version: 4.5 Mesa 19.2.8 (compat-v: 3.0) Direct Render: Yes

```
```
$ xrandr --listproviders
Providers: number : 1
Provider 0: id: 0x46 cap: 0x9, Source Output, Sink Offload crtcs: 3 outputs: 4 associated providers: 0 name:modesetting
```
```
*-display
description: VGA compatible controller
product: Intel Corporation
vendor: Intel Corporation
physical id: 2
bus info: pci@0000:00:02.0
version: 02
width: 64 bits
clock: 33MHz
capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
configuration: driver=i915 latency=0
resources: irq:134 memory:50000000-50ffffff memory:40000000-4fffffff ioport:3000(size=64) memory:c0000-dffff
```

My immediately previous build had a still-running 10 year old Gigabyte board with intel graphics and a VGA port - to the same monitor - with crisper rendering (though the cpu was starting to struggle to keep up).

Perhaps, there are things I still need to address to configure the new system / onboard graphics properly?

Thanks for any suggestions.

---

### Post by thehipho on 2020-02-26
> 
Images and video seem clear, smooth and hi-res.

However, the rendering of fonts and other graphical elements, logos, spreadsheets, menus - is grainy / low res / pixelated - and, certainly, not what I'd expect from this latest generation of hardware.

The display resolution is set to 1920 x 1080 @ 60hz and connected via HDMI (at both ends).

I have also fiddled with the rendering / anti-aliasing appearance settings - without success.



Have you tried manually adjusting color setting on the monitor including brightness and sharpness(should take care of grainy issue)?

---

### Post by maclenin on 2020-03-01
Thanks for the note!

I have fiddled with the manual settings, as you suggest (among the usual others - contrast, tint, etc) - but always feel like the little dutch boy at the dike - plugging one hole (spreadsheet render improvement) yields another (color blow out in the browser)....

Resetting to default monitor settings - also doesn't cut it.

Perhaps, my eyes deceive me....

Thanks, again, for the suggestions!

---

### Post by thehipho on 2020-03-01
As a suggestion you could try different DE's, you might see some improvements. 
My favorites DE's are KDE Plasma, and Gnome. Obviously they're not as lightweight as XFCE.
You might want try them in live mode first?

---

