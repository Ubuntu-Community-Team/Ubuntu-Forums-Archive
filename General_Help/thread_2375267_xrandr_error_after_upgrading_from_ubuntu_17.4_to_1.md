---
title: "xrandr error after upgrading from ubuntu 17.4 to 17.10"
date: 2017-10-23
forum: General Help
---

### Post by laassari on 2017-10-23
I was using this little script to fix the resolution of my screen since ubuntu fails to detect it
```

xrandr --newmode "1440x900_60.00"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
xrandr --addmode VGA-1 1440x900_60.00
xrandr --output VGA-1 --mode 1440x900_60.00

```

This is not working anymore after upgrading to Ubuntu 17.10 and I'm stuck at 1024x168

the following error appears when I execute this script
```
X Error of failed request:  BadName (named color or font does not exist)  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  16 (RRCreateMode)
  Serial number of failed request:  18
  Current serial number in output stream:  18
xrandr: cannot find output "VGA-1"
warning: output VGA-1 not found; ignoring
```

after trying several solutions online I got a new error:
```
xrandr: Configure crtc 0 failed
```

---

### Post by wahaj007 on 2017-12-10
same problem with me

---

### Post by ajgreeny on 2017-12-10
Try logging into the xorg session from the login screen.
Wayland which is the default for 17.10 has known problems with many, if not all, xsession utilities, which is no surprise as there is no X running.

---

