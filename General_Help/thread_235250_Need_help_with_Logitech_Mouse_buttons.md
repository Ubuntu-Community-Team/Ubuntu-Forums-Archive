---
title: "Need help with Logitech Mouse buttons"
date: 2006-08-12
forum: General Help
---

### Post by spacepirates on 2006-08-12
After many futile hours trying to get my Logitech mx 310 (mx310) buttons to become back and forward i ended my pursuit. only to find that the mouse's buttons had switched. the scroll wheel no longer works, and in its place are the two side buttons, now functioning as the scroll wheel.

I have reconfigured xorg.conf and am fairly sure any other changes made during the button config process were undone.

can anyone help solve this problem?

it is remarkably annoying not having a scroll wheel...

---

### Post by wieman01 on 2006-08-12
> **spacepirates said:**
> After many futile hours trying to get my Logitech mx 310 (mx310) buttons to become back and forward i ended my pursuit. only to find that the mouse's buttons had switched. the scroll wheel no longer works, and in its place are the two side buttons, now functioning as the scroll wheel.

I have reconfigured xorg.conf and am fairly sure any other changes made during the button config process were undone.

can anyone help solve this problem?

it is remarkably annoying not having a scroll wheel...

This is a nice little howto that should help resolve your problem. I've used it before:

[http://www.ubuntuforums.org/showthread.php?t=188302]("http://www.ubuntuforums.org/showthread.php?t=188302")

---

### Post by spacepirates on 2006-08-13
I tried this guide, but X still crashes with the error /dev/wacom file or directory does not exist. there are three more input devices (aside from mouse, keyboard, and speakers) and when i tried commenting them out X crashed. 

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

i don't know what they are, but i do know commenting them out crashes X. any ideas?

---

### Post by wieman01 on 2006-08-13
Oh, your're right. You don't need "wacom" and it should be safe to throught it out. I did the same with mine. Let us know if that causes a problem. I attached my "xorg.conf" file for reference.

---

