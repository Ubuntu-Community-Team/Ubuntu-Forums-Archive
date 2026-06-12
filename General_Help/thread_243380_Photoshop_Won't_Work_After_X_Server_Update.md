---
title: "Photoshop Won't Work After X Server Update"
date: 2006-08-25
forum: General Help
---

### Post by fishmorg909 on 2006-08-25
Well, like lots of other folks, I got the bad X server update, then got the good one. My computer runs fine again, except now Photoshop 7 no longer loads. It was working well with Wine... but after the X server mess, PS won't load, even though ImageReady does. I tried starting it in terminal, and got this:
```
me@mycomp:~/.wine/drive_c/Program_Files/Adobe/Photoshop_7$ sudo wine photoshop
fixme:actctx:QueryActCtxW stub!
X Error of failed request:  BadDevice, invalid or uninitialized input device
  Major opcode of failed request:  144 (XInputExtension)
  Minor opcode of failed request:  3 (X_OpenDevice)
  Serial number of failed request:  34
  Current serial number in output stream:  34
```
I tried a full reinstall of both Wine and Photoshop -- still nothing. Any suggestions? Thanks.

---

### Post by Subbu.exe on 2006-08-25
Its got something to do with wacom, a input device for Tablet PC's i guess..

Type **sudo gedit /etc/X11/xorg.conf**

and Delete these Lines
```
Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

```

and these in the "ServerLayout" Section at the bottom of the file.
```

	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"

```

Save and Reboot X.

---

### Post by fishmorg909 on 2006-08-25
Thanks, subbu.exe, that did the trick -- Photoshop is up and running again! :cool:

---

