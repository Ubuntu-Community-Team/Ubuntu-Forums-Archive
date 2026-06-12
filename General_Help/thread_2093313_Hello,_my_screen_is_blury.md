---
title: "Hello, my screen is blury"
date: 2012-12-10
forum: General Help
---

### Post by Chad De Lange on 2012-12-10
Hello, My screen is blury.

I have ubuntu 12, with gnome-shell. uninstalled unity

Here is a screen shot

[img]http://s.ikat.me/1yV1Ty.png[/img]

I also attached the image

Are there any commands I should run, that you would like to see the output of.

Thanks

---

### Post by Monotoko on 2012-12-10
The screenshot looks fine here (but I haven't slept for over 24 hours now :P) - so I'd be inclined to think it's a graphics card issue on your end, can you tell me what graphics card you have?

---

### Post by Chad De Lange on 2012-12-10
Hmm, you're right, when I open the picture on a other computer it looks fine...

Guess it's my screen then

Don't have a graphics card but here is the output of sudo lshw -C video


  *-display               
       description: VGA compatible controller
       product: 82Q963/Q965 Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:42 memory:d0000000-d00fffff memory:c0000000-cfffffff ioport:3400(size=8)

---

### Post by Impavidus on 2012-12-10
Intel integrated graphics work fine most of the time (for me anyway, although I don't have exactly the same chipset). Are you using 12.04 precise or 12.10 quantal? My graphics work fine without manual changes on 12.04 now, but just after the upgrade to 12.04 (and just after upgrades to 11.10 and 11.04) I had some problems (which got solved automatically). If you're using 12.10 it could well be a driver problem, on 12.04 that's unlikely to happen.

---

### Post by Chad De Lange on 2012-12-11
I'm using 12.04

And incase this has anything to do with the blury screen.

When ever I restart the computer I have to run these commands to get my screen resolution right

`gtf 1440 900 60|grep Modeline|sed -e's|Modeline|xrandr --newmode|'`

xrandr --addmode VGA1 '"1440x900_60.00"'

---

