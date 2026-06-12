---
title: "Matching NVIDIA display settings with XFCE display settings."
date: 2022-06-01
forum: General Help
---

### Post by makem2 on 2022-06-01
```

makem@makem2204:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 22.04 LTS
Release:    22.04
Codename:    jammy
makem@makem2204:~$nvidia-settings


(nvidia-settings:5772): GLib-GObject-CRITICAL **: 00:06:06.178: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
** Message: 00:06:06.282: PRIME: Requires offloading
** Message: 00:06:06.282: PRIME: is it supported? yes
** Message: 00:06:06.298: PRIME: Usage: /usr/bin/prime-select nvidia|intel|on-demand|query
** Message: 00:06:06.298: PRIME: on-demand mode: "1"
** Message: 00:06:06.298: PRIME: is "on-demand" mode supported? yes

```

I am using a dual screen setup and I gather that I must match settings in XFCE and NVIDIA settings to retain display setting over reboots.

I can set the XFCE display settings using the 'Display' option in Ubuntu Settings manager and apparently I can set NVIDIA setting using the terminal command 'nvidia-settings'.

The NVIDIA settings are greyed out and show that screen 1 is PRIME: DP-1-1 and screen 2 is PRIME: HDMI-1-1

There is a note below which says:

PRIME Displays cannot be controlled by nvidia-settings and must be configured by an external RandR capable tool. The display shown in the layout window is for informational purposes only.

I chose to use NVIDIA driver metapackage from nvidia-driver-510 (proprietary tested) from Additional Drivers in the Repositories. Why is PRIME involved? Can I remove it and use the GFX card driver I chose?

I have to reset the XFCE settings every time I reboot because they default to Mirror Displays and a refresh rate of 60 Hz for both screens.

---

### Post by Yellow Pasque on 2022-06-02
I've had issues with xfce not saving my resolution settings before. IIRC, I had to delete the displays.xml file and then go into the xfce display settings and configure them (so a fresh displays.xml gets generated):
```
rm ~/.config/xfce4/xfconf/xfce-perchannel-xml/displays.xml
```

> Why is PRIME involved? Can I remove it?

Probably because you have a laptop with hybrid Intel/Nvidia graphics. If so, don't try and remove it. Prime is what allows you to switch between GPU's and disables the Nvidia GPU when not in use to save power.

---

### Post by makem2 on 2022-06-04
> **Yellow Pasque said:**
> I've had issues with xfce not saving my resolution settings before. IIRC, I had to delete the displays.xml file and then go into the xfce display settings and configure them (so a fresh displays.xml gets generated):
```
rm ~/.config/xfce4/xfconf/xfce-perchannel-xml/displays.xml
```



Probably because you have a laptop with hybrid Intel/Nvidia graphics. If so, don't try and remove it. Prime is what allows you to switch between GPU's and disables the Nvidia GPU when not in use to save power.

I will try removing displays.xml and configuring the display settings as you suggest.

As for PRIME: The computer in question is a desktop, not a laptop. Is PRIME something separate from the NVIDIA drivers and gets added automatically or by choice? I don't recollect choosing to use PRIME.

---

### Post by Yellow Pasque on 2022-06-04
Then it's strange that nvidia-prime reports those messages, unless you have a premade desktop configured that way.

---

### Post by makem2 on 2022-06-05
> **Yellow Pasque said:**
> Then it's strange that nvidia-prime reports those messages, unless you have a premade desktop configured that way.

The desktop is just default of the OS. No changes made.

However, the Display settings are now retained since the new [COLOR=#000000][FONT=&quot]displays.xml file.

[/FONT][/COLOR]Thank you.

---

### Post by makem2 on 2022-06-06
> **makem2 said:**
> The desktop is just default of the OS. No changes made.

However, the Display settings are now retained since the new [COLOR=#000000][FONT=&amp]displays.xml file.

[/FONT][/COLOR]Thank you.

I spoke to soon!

If I turn of the main monitor, leaving the PC running, when I come back Display is asking if I want to keep the current settings and I find the display is mirrored. Also it has forgotten the [COLOR=#000000]refresh rate.[/COLOR]

---

### Post by Yellow Pasque on 2022-06-06
> **makem2 said:**
> I spoke to soon!

If I turn off the main monitor, leaving the PC running, when I come back Display is asking if I want to keep the current settings and I find the display is mirrored. Also it has forgotten the refresh rate.

I don't have a lot of experience with multi-monitor, but it sounds like if you have an extended desktop, and you take the primary display out of the equation, the secondary one becomes a solo display and goes to its preferred mode. It seems like reasonable behavior to me.

---

### Post by makem2 on 2022-06-06
> **Yellow Pasque said:**
> I don't have a lot of experience with multi-monitor, but it sounds like if you have an extended desktop, and you take the primary display out of the equation, the secondary one becomes a solo display and goes to its preferred mode. It seems like reasonable behaviour to me.

I follow your reasoning. The 'main' display (143.9 Hz) has the number (2) and has a DP connection. The secondary display has the number (1) and defaults to 60 Hz.

I don't use the secondary display every time I start the PC (It is still connected with an HDMI connection).

I think the 'main' display should be number (1) but cannot see how to change it. I don't know if this has any bearing.

If I turn both monitors on before booting then the secondary display always comes on seconds before the 'main' display.  At that time the displays are mirrored. Windows deals with that correctly but Ubuntu needs help. With just the 'main' on Ubuntu as I have said, now uses the correct Hz so it is a shame it fails when the display has been on standby.

---

