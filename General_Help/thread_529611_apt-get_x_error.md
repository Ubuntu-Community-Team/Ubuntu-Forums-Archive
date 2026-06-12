---
title: "apt-get x error"
date: 2007-08-19
forum: General Help
---

### Post by antisho on 2007-08-19
Many times when I use apt-get, it spits out error messages like

```
X Error: BadDevice, invalid or uninitialized input device 170
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 170
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
```

which don't seem to affect the installation in any way, but are they a sign of a problem? Is there a way to get rid of them?

---

### Post by sumguy231 on 2007-08-19
That's a generally harmless message that tells you that there's an input device in your X configuration that is not actually present. It seems to usually be caused by references to Wacom tablets in xorg.conf. You can probably ignore it, but if you don't have a Wacom tablet and really want to get rid of it you'll need to edit /etc/X11/xorg.conf, and comment out these sections by placing a # in front of each line:
```
#Section "InputDevice"
#       Driver          "wacom"
#       Identifier      "stylus"
#       Option          "Device"        "/dev/input/wacom"
#       Option          "Type"          "stylus"
#       Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
#EndSection
```
Do this for all sections with the "Driver   '"wacom'"  line in them. You'll also need to comment out the part that says:
```
#       InputDevice     "stylus"        "SendCoreEvents"
#       InputDevice     "cursor"        "SendCoreEvents"
#       InputDevice     "eraser"        "SendCoreEvents"
```
You need to do this especially or X won't start. This section is toward the bottom in the "ServerLayout" section.

By the way, you can edit that file by running
```
gksu gedit /etc/X11/xorg.conf
```

It's odd that you're getting it when running apt-get though, since that's not even graphical. It could still happen if you ran something graphical from the terminal and then apt-get.

---

### Post by antisho on 2007-08-19
All right, thanks! :)

---

### Post by g2g591 on 2007-08-21
Thanks from me too, I've been wanting to get rid of those for a while

---

