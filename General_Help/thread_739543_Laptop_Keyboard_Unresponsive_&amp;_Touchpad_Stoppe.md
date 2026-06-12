---
title: "Laptop Keyboard Unresponsive &amp; Touchpad Stopped"
date: 2008-03-29
forum: General Help
---

### Post by gladstone on 2008-03-29
Firsty, I'm using an Acer laptop with a Synaptics touchpad. A few weeks ago, the touchpad decided to stop working all-together (which I didn't notice for a while since I happily use a USB mouse without any trouble).

If I dual-boot into Windows, the touchpad still does not work, which is kind of worrying...

To make matters worse, my laptop keyboard has now become periodically unresponsive. As I'm typing now, periodically some letters will not appear and will miss them all-together. Frankly, it is the most annoying thing ever!

This thread sounds like a similar issue:

[http://ubuntuforums.org/showthread.php?t=416852](http://ubuntuforums.org/showthread.php?t=416852)

Steps I've taken to try solve it:

[LIST=1]
[*]Checked to see if "Slow Keys" was enabled - **No**
[*]If I check in /usr/logs/syslog, I can see this:

```
Mar 29 23:47:41 tom-laptop kernel: [ 5545.492000] input: PS/2 Synaptics TouchPad as /class/input/input1501

Mar 29 23:47:43 tom-laptop NetworkManager: <debug> [1206834463.460645] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input'). 

Mar 29 23:47:44 tom-laptop kernel: [ 5547.728000] Unable to query Synaptics hardware.
```

and with Thunar (running from a terminal):

```
thunar-volman: No device with id /org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input.
```

Looking at those timestamps, they (kind of) match up with when my keyboard "misses" the letters I type.
[/LIST]
[SIZE="1"]*(Now that was a short list eh? :()*[/SIZE]

Any ideas? :confused:

---

### Post by |{urse on 2008-03-29
since the hardware abstraction layer isnt seeing it at all you may want to google for a disassembly manual (most all laptop models have them) and be sure the ribbon connecting your keyboard into its zif socket isn't loose or disconnected. also check in your bios to see if there isnt a way to enable/re-enable the touchpad, seems i remember that working on an old dell laptop of mine. Also, did you recently change your xorg.conf?

---

### Post by |{urse on 2008-03-29
also try a 

sudo dpkg-reconfigure xserver-xorg

---

### Post by |{urse on 2008-03-29
> If I dual-boot into Windows, the touchpad still does not work, which is kind of worrying...

OH! i hadnt seen tht.. well id say its most probably dying or "mis-connected" got get your tiny screwdriver  ^^

---

### Post by gladstone on 2008-04-02
Well I had a go a taking the laptop apart...

It's an Acer Extensa 6602 and there really is very little about the laptop on the 'net.

I managed (after a fair few hours) to get it open. Had a look at the touchpad and keyboard connectors, but they look fine - albeit I moved them around abit just to check.

It seems Acer themselves put a "supervisor password" on their laptops, which has locked me out of the "advanced" section of the BIOS - where I expect I can disable the touchpad.

After finding [this site]("http://www.vietzon.com/red/?p=92") I had a look around inside for a dip-switch to no avail :( I'm gonna try taking the battery out to clear the CMOS, but from the 10 minutes I did have it out, it didn't clear the password. I've heard though, that you need to leave laptop batts. out for 24 hours, so I'll try that.

Meanwhile though, (after struggling to put it all back together) my keyboard seems to be back to normal (no unresponsive-ness) which is great! Touchpad still doesnt work... but I'm not too bothered about that.

---

