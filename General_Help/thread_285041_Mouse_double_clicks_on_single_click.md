---
title: "Mouse double clicks on single click"
date: 2006-10-26
forum: General Help
---

### Post by h20Boodle on 2006-10-26
My mouse is intermittently interpreting my single clicks as double clicks. I have tried setting the System->Preferences->Mouse Double-Click timeout to the smallest value (100mS), but it still doesn't always work as expected. I've also replaced my mouse with a brand new one, and have tried both the USB and PS/2 ports on my PC.

I'm running: Linux 2.6.15-27-386 and Ubuntu 6.06.

"dmesg" shows the following info on my mouse:
input: Microsoft Microsoft 5-Button Mouse with IntelliEye(TM) as /class/input/input1
input: USB HID v1.10 Mouse [Microsoft Microsoft 5-Button Mouse with IntelliEye(TM)] on usb-0000:00:03.1-1

My xorg.conf file has this entry for the mouse:
Section "InputDevice"
  Identifier  "Configured Mouse"
  Driver    "mouse"
  Option    "CorePointer"
  Option    "Device"    "/dev/input/mice"
  Option    "Protocol"    "ExplorerPS/2"
  Option    "ZAxisMapping"    "4 5"
  Option    "Emulate3Buttons" "false"
EndSection

Any ideas on how I can fix this problem? It's driving me crazy!

Thanks.

---

### Post by sn0w on 2006-11-11
I am having the exact same problem in 6.10 with 2.6.17-10-generic. My xorg.conf is also identical except I have "Emulate3Buttons" set to true.

---

### Post by williecdog on 2006-11-21
Same problem here, unfortunately.  It is an intermittent problem, there is no way I can tell exactly when the double-click occurs.  I'm on 6.10, kernel 2.6.17-10-386.  Here are my mouse settings in the xorg.conf file:

Section "InputDevice"
   Identifier  "Configured Mouse"
   Driver      "mouse"
   Option      "CorePointer"
   Option      "Device"    "/dev/input/mice"
   Option      "Protocol"     "ImPS/2"
   Option      "Emulate3Buttons" "true"
   Option      "ZAxisMapping"    "4 5"
EndSection

dmesg:
input: Logitech USB Optical Mouse as /class/input/input1
input: USB HID v1.10 Mouse [Logitech USB Optical Mouse] on usb-0000:00:07.2-2

Xorg:
X Window System Version 7.1.1

---

### Post by h20Boodle on 2008-02-18
Coming back to this many months later ... It was simply bad hardware. A new mouse did resolve the problem despite what I said in my initial post.

---

### Post by xjgnsdof on 2008-05-21
I had this problem on my HP Mini-Note 2133. I edited the /etc/X11/xorg.conf and added the following line under the Input Device section for my mouse:

```
Option          "CorePointer"
```

Apparently, there has to be one pointing device, whether it be a touchpad or a standard mouse, that is designated as the "CorePointer." After a reboot, my clicking issue was resolved.

If you try this, make sure to back up your original xorg.conf file, as I was using an OpenSUSE xorg.conf file in Ubuntu when my problem arose (for 3D graphics purposes).

---

### Post by nquinnathome1 on 2008-05-22
I've got the same problem; my clicks randomly become double clicks. Amending my xorg.conf with
```

Option "CorePointer"
```
hasn't made a difference either.

EDIT:

I've found another solution which works on several of my Hardy machines...

Enter the following into your xorg.conf file (replacing the existing mouse section) - you need both sections:
```

Section "InputDevice"
    Identifier     "CorePointer"
    Driver         "mouse"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "Emulate3Buttons" "true"
EndSection

```

---

### Post by clubsoda on 2008-06-09
Seems strange to have to Emulate3Buttons for a mouse which already has a full complement of 3 buttons...

I didn't need the CorePointer section at all - simply added the Emulate3Buttons line to the Configured Mouse section.

False double-clicks greatly reduced, thanks.

---

