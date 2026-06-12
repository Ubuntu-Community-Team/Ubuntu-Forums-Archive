---
title: "xubuntu standby, suspend issue"
date: 2007-05-18
forum: General Help
---

### Post by ShirishAg75 on 2007-05-18
Hi all,
    How can I set standby, shutoff in xubuntu? 

xset q shows me this :-

```
 xset q
Keyboard Control:
  auto repeat:  on    key click percent:  0    LED mask:  00000000
  auto repeat delay:  500    repeat rate:  30
  auto repeating keys:  00ffffffdffffbbf
                        fadfffdfffdfe5ef
                        ffffffffffffffff
                        ffffffffffffffff
  bell percent:  50    bell pitch:  400    bell duration:  100
Pointer Control:
  acceleration:  2/1    threshold:  4
Screen Saver:
  prefer blanking:  yes    allow exposures:  yes
  timeout:  0    cycle:  0
Colors:
  default colormap:  0x20    BlackPixel:  0    WhitePixel:  16777215
Font Path:
  /usr/share/fonts/X11/misc,/usr/share/fonts/X11/100dpi/:unscaled,/usr/share/fonts/X11/75dpi/:unscaled,/usr/share/fonts/X11/Type1,/usr/share/fonts/X11/100dpi,/usr/share/fonts/X11/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,/usr/share/fonts/X11/misc,/usr/share/fonts/X11/100dpi/:unscaled,/usr/share/fonts/X11/75dpi/:unscaled,/usr/share/fonts/X11/Type1,/usr/share/fonts/X11/100dpi,/usr/share/fonts/X11/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
Bug Mode: compatibility mode is disabled
DPMS (Energy Star):
  Standby: 0    Suspend: 0    Off: 0
  DPMS is Enabled
  Monitor is On
File paths:
  Config file:  /etc/X11/xorg.conf
  Modules path: /usr/lib/xorg/modules
  Log file:     /var/log/Xorg.0.log

```

While if you see this image of xscreensaver-demo I did some changes :-

[IMG]http://img242.imageshack.us/img242/6046/xscreensaverpreferencestu4.png[/IMG]


Please lemme know if this can be changed in anyway, thank you all.

---

### Post by badtlc on 2007-06-30
I have the same problem.  Can anyone help?

---

### Post by ShirishAg75 on 2007-07-07
There is something called suspend2 which is supposed to be better. Its there in gutsy but dunno how it works.... yet.

---

### Post by cleavor07 on 2008-02-09
I had a similar problem.

I know what I am going to suggest is really simple, but did you try using (from the terminal):

sudo vim \etc\default\acpi-support

edit the line that reads acpi_sleep_mode=mem

change mem to standby

---

### Post by micah on 2008-06-03
I'm tried editing the line in \etc\default\acpi-support  and i still had the same problem.  The hard drive spins back up and the CPU fan kicks on. But there is not signal detected by my monitor.

I'm running xubuntu 8.04 and have a nVidia card and driver installed if that makes a difference.  

Any help for this newb would be appreciated.

---

