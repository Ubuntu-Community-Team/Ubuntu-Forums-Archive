---
title: "No native resolution option in display settings"
date: 2020-09-22
forum: General Help
---

### Post by andrei-micuda on 2020-09-22
Hello!
I have been using Ubuntu Budgie for about 2 weeks now and enjoy it very  much, but I have encountered a slightly annoying problem. Recently, I  realized that the resolution on my laptop monitor is set to 1920x1080,  when my native resolution is 1600x900, with no option for native  resolution in the dropdown list. The strange thing is that on my second  monitor (which has a native resolution of 1920x1080), the 1600x900 entry  is listed in the resolution list. I have tried adding a custom  resolution using xrandr, but although the resolution appears in the list  now, if I select it, the display just goes black (the other one still  works) and I have to wait for the system to revert my resolution to be  able to use that screen again.
Thanks in advance for your help!

---

### Post by TheFu on 2020-09-22
Please show the exact **xrandr** command attempted. The xrandr output showing the modes and connected monitors would be good too. Please.

I use this on a 1920x1200 monitor with a connect that supports that resolution:
```
xrandr --output DVI-D-0 --mode 1920x1200
```

And for a virtual machine, I use this:
```
xrandr --output Virtual-1  --mode 1680x1050
```

After you set the exact resolution you want that also works, just put the command into the ~/.xprofile file.  You may need to create this file in your HOME directory. It is one of those files that gets run whenever X11 starts.  I don't know whether Wayland pays attention or not.

If the xorg.conf file doesn't have the correct modeline for the resolution - usually provided directly by the monitor connection - then X11 should refuse the command. In the early days, driving a monitor at incorrect settings could break the monitor forever, never to work again.

Modelines have all sorts of numbers in them. I don't know how to get the correct numbers except from the EDID provided directly by the monitor when powered on or from the manufacturer.  There are tools to dump the EDID data, **get-edid**, which can be forced to be used if the connection is too complex to provide it. I connect to that 1200p monitor through a VGA cable, through a KVM switch, through a DVI-to-VGA converter from a DVI-d connector on an nVidia GT 1030 GPU. That proved to be too much for the EDID to get faithfully passed. The DVI-to-VGA converter was making up lower resolution EDID data, so I had to force it to what the monitor reported when connected to a different system directly via VGA cable.

Again, I have no idea how this works with Wayland. Sorry.

---

