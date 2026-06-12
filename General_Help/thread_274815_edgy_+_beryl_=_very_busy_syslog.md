---
title: "edgy + beryl = very busy syslog"
date: 2006-10-10
forum: General Help
---

### Post by keredson on 2006-10-10
hey all,

i'm using edgy + beryl + aiglx, and everything works, except that syslogd is churning through gigabytes of the following:

```
...
[17207082.756000] i915_emit_cmds(374)
[17207082.756000] i915_emit_cmds(369)
[17207082.756000] i915_emit_cmds(374)
[17207082.756000] i915_emit_cmds(369)
[17207082.756000] i915_emit_cmds(374)
[17207082.756000] i915_emit_cmds(369)
[17207082.756000] i915_emit_cmds(374)
[17207082.756000] i915_emit_cmds(369)
[17207082.756000] i915_emit_cmds(374)
[17207082.756000] i915_emit_cmds(369)
[17207082.756000] i915_emit_cmds(374)
...
```

relevant details:

```
derek@kaylee:~$ lspci | grep -i graph
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
```

```
derek@kaylee:~$ cat /etc/X11/xorg.conf
...
Section "Module"
#       Load    "GLcore"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "dbe"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection
...
Section "Device"
        Identifier      "Intel Corporation 82852/855GM Integrated Graphics Device"
        Driver          "i810"
#       BusID           "PCI:0:2:0"
        Option  "XAANoOffscreenPixmaps"
EndSection
...
Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "Synaptics Touchpad"
        Option         "AIGLX" "true"
EndSection

Section "DRI"
        Mode    0666
EndSection

Section "Extensions"
#        Option "Composite" "Enable"
        Option "Composite" "True"
EndSection
```

any ideas?

thanks!
derek

---

### Post by ayoli on 2006-10-10
this is a known bug, there is a thread about it here:
[http://www.ubuntuforums.org/showthread.php?t=274386](http://www.ubuntuforums.org/showthread.php?t=274386)
and a bug filled on launchpad here:
[https://launchpad.net/distros/ubuntu/+bug/64970](https://launchpad.net/distros/ubuntu/+bug/64970)

---

### Post by keredson on 2006-10-10
thanks!

---

