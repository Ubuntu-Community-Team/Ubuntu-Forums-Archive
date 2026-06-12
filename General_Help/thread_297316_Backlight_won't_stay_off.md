---
title: "Backlight won't stay off"
date: 2006-11-10
forum: General Help
---

### Post by konradsa on 2006-11-10
Hi,

I upgraded from Dapper to Edgy, and since then I have some problems on my laptop (HP dv1340 with i915) of keeping the LCD backlight off. The problem is the following:

xset q output:
```

Keyboard Control:
  auto repeat:  on    key click percent:  0    LED mask:  00000000
  auto repeat delay:  500    repeat rate:  30
  auto repeating keys:  00ffffffdffffbbf
                        fadfffdfffdfe5ef
                        ffffffffffffffff
                        ffffffffffffffff
  bell percent:  50    bell pitch:  400    bell duration:  100
Pointer Control:
  acceleration:  3/2    threshold:  5
Screen Saver:
  prefer blanking:  yes    allow exposures:  yes
  timeout:  0    cycle:  0
Colors:
  default colormap:  0x20    BlackPixel:  0    WhitePixel:  16777215
Font Path:
  /usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fonts/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/usr/share/fonts/X11/misc,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,/usr/share/fonts/X11/misc/,/usr/share/fonts/X11/Type1/,/usr/share/fonts/X11/100dpi/,/usr/share/fonts/X11/75dpi/
Bug Mode: compatibility mode is disabled
DPMS (Energy Star):
  Standby: 5    Suspend: 5    Off: 5
  DPMS is Enabled
  Monitor is On
File paths:
  Config file:  /etc/X11/xorg.conf
  Modules path: /usr/lib/xorg/modules
  Log file:     /var/log/Xorg.0.log


``` 

So now I can go and set 

```

xset dpms 5 5 5 

```

(5 secs for testing, it doesn't matter what value I choose). The LCD then turns off completely after 5 seconds, but after about a 30 secs to a minute (around that much, I haven't used a stopwatch yet) the backlight comes back on again, but the screen remains blank until I move the mouse or click a button, So something is turning on the backlight again. I doubt it's a keyboard or mouse event, as this would also unblank the screen. Changing the Settings in System - Preferences - Screensaver or xorg.conf has the same effect, backlight turns off for a minute at most and comes back on again permanently.

Does anybody have an idea how to fix it?

---

### Post by konradsa on 2006-11-11
Ok,

I think I found a workaround for this problem, so I am posting it here for people that also have this problem, I saw there were a couple in the forum.

I noticed that every time the backlight turns back on, an event is stored in /var/log/acpid. This event looks like this

```
[Sat Nov 11 09:07:44 2006] received event "battery BAT0 00000080 00000000"
[Sat Nov 11 09:07:44 2006] notifying client 3994[113:115]
[Sat Nov 11 09:07:44 2006] executing action "/etc/acpi/power.sh"
[Sat Nov 11 09:07:44 2006] BEGIN HANDLER MESSAGES
[Sat Nov 11 09:07:44 2006] END HANDLER MESSAGES
[Sat Nov 11 09:07:44 2006] action exited with status 0
[Sat Nov 11 09:07:44 2006] executing action "/etc/acpi/actions/lm_battery.sh battery BAT0 00000080 00000000"
[Sat Nov 11 09:07:44 2006] BEGIN HANDLER MESSAGES
[Sat Nov 11 09:07:44 2006] END HANDLER MESSAGES
[Sat Nov 11 09:07:44 2006] action exited with status 0
[Sat Nov 11 09:07:44 2006] completed event "battery BAT0 00000080 00000000"
[Sat Nov 11 09:07:44 2006] received event "battery BAT0 00000000 00000000"
[Sat Nov 11 09:07:44 2006] notifying client 3994[113:115]
[Sat Nov 11 09:07:44 2006] executing action "/etc/acpi/power.sh"
[Sat Nov 11 09:07:44 2006] BEGIN HANDLER MESSAGES
[Sat Nov 11 09:07:44 2006] END HANDLER MESSAGES
[Sat Nov 11 09:07:44 2006] action exited with status 0
[Sat Nov 11 09:07:44 2006] executing action "/etc/acpi/actions/lm_battery.sh battery BAT0 00000000 00000000"
[Sat Nov 11 09:07:44 2006] BEGIN HANDLER MESSAGES
[Sat Nov 11 09:07:44 2006] END HANDLER MESSAGES
[Sat Nov 11 09:07:44 2006] action exited with status 0
[Sat Nov 11 09:07:44 2006] completed event "battery BAT0 00000000 00000000"
[Sat Nov 11 09:07:44 2006] received event "ac_adapter ACAD 00000000 00000001"
[Sat Nov 11 09:07:44 2006] notifying client 3994[113:115]
[Sat Nov 11 09:07:44 2006] executing action "/etc/acpi/actions/lm_ac_adapter.sh ac_adapter ACAD 00000000 00000001"
[Sat Nov 11 09:07:44 2006] BEGIN HANDLER MESSAGES
Laptop mode disabled, not active.
[Sat Nov 11 09:07:44 2006] END HANDLER MESSAGES
[Sat Nov 11 09:07:44 2006] action exited with status 0
[Sat Nov 11 09:07:44 2006] executing action "/etc/acpi/power.sh"
[Sat Nov 11 09:07:44 2006] BEGIN HANDLER MESSAGES
[Sat Nov 11 09:07:44 2006] END HANDLER MESSAGES
[Sat Nov 11 09:07:44 2006] action exited with status 0
[Sat Nov 11 09:07:44 2006] completed event "ac_adapter ACAD 00000000 00000001"
```

This event seems to be related to my laptop, which seems to post some battery-related events every minute (even w/o a battery in it).

The bug is actually described here:
[https://bugzilla.novell.com/show_bug.cgi?id=197858](https://bugzilla.novell.com/show_bug.cgi?id=197858)

So a bug report has been filed and people are working on it. Temporary workaround is to set the option 

```

	Option       	"NoPM" "yes"

```

in the ServerLayout section of /etc/X11/xorg.conf. The power management still works under GNOME, but I am not sure if that completely disables power management under GDM (i.e., when not logged in).

---

### Post by alonso on 2006-11-16
This seems to be fixed in xorg 7.2:

[https://bugs.freedesktop.org/show_bug.cgi?id=5665](https://bugs.freedesktop.org/show_bug.cgi?id=5665)

I hope somebody shows how to compile this version when it is released.

---

### Post by alonso on 2006-11-16
d

---

### Post by konradsa on 2006-11-16
> **alonso said:**
> This seems to be fixed in xorg 7.2:

[https://bugs.freedesktop.org/show_bug.cgi?id=5665](https://bugs.freedesktop.org/show_bug.cgi?id=5665)

I hope somebody shows how to compile this version when it is released.

Good,

Do you know if that is sufficient, or we need to file a bug report so that the Ubuntu team can backport the fix? I checked the Ubuntu bug database here

[https://launchpad.net/distros/ubuntu/+source/xorg](https://launchpad.net/distros/ubuntu/+source/xorg)

and could not find any mentioning of the bug.

-- Sascha

---

### Post by alonso on 2006-11-17
I think this is serious problem: this will burn laptop screens in the long run.

So yes: we should definitely file a bug report in order to get this backported.

---

### Post by konradsa on 2006-11-17
> **alonso said:**
> I think this is serious problem: this will burn laptop screens in the long run.

So yes: we should definitely file a bug report in order to get this backported.

Ok, if anybody knows how to do this properly, then go ahead please. Otherwise I will try to figure it out this weekend, I have never done that before.

-- Sascha

---

### Post by alonso on 2006-11-17
Submitted the bug:

[https://launchpad.net/distros/ubuntu/+source/xorg/+bug/72231](https://launchpad.net/distros/ubuntu/+source/xorg/+bug/72231)

---

### Post by n888 on 2007-03-26
[QUOTE=konradsa;1743790]
```

	Option       	"NoPM" "yes"

```


THANKS konradsa! This fixed my problem.

Note to others: I had to put this under the **ServerLayout** section in order for it to work.

---

### Post by json684 on 2007-04-22
Thank you so very much. You are a god.

---

