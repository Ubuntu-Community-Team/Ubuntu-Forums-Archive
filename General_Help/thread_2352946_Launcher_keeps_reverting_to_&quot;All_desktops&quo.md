---
title: "Launcher keeps reverting to &quot;All desktops&quot; in Unity Tweak Tool"
date: 2017-02-17
forum: General Help
---

### Post by phenomenos2 on 2017-02-17
Hi. First of all, sorry if I posted in the wrong board - I'm new to this forum.

I am running Ubuntu 16.10 with a two monitor set up. I used Unity Tweak Tool to auto-hide the launcher and set it to show only on my primary desktop. It has functioned perfectly fine like this for weeks. Then suddenly today it began showing on my second screen as well, which is super annoying because the mouse sometimes "sticks" when I'm moving it between screens. Every time I open Unity Tweak Tool, go to the launcher settings, and click "Primary desktop" nothing happens - the launcher still shows on my second screen. And if I close and reopen Unity Tweak Tool then "All desktops" is selected again.

Has anyone else encountered this problem? Any idea what's causing it and how I could fix it?

EDIT: I have tried removing and reinstalling Unity Tweak Tool. No change.

---

### Post by DuckHook on 2017-02-17
Welcome to the forums, phenomenos2.

In System settings&#8594;Screen Display, which monitor is "Launcher placement" set at?

Please provide complete HW info. For type of info required, please see my sig: *How to Ask for Help*

Please post output of ```
xrandr
``````
lspci -vk | grep -iA13 vga
```

Did you install an update or app before it started acting strangely? Did you change any system settings? Any coincidental power outtages or brownouts?

---

### Post by phenomenos2 on 2017-02-20
xrandr:

```
Screen 0: minimum 320 x 200, current 3840 x 1080, maximum 8192 x 8192
VGA-1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 510mm x 290mm
   1920x1080     60.00*+
   1680x1050     59.95  
   1280x1024     75.02    60.02  
   1152x864      75.00  
   1024x768      75.03    60.00  
   800x600       75.00    60.32  
   640x480       75.00    59.94  
   720x400       70.08  
HDMI-1 disconnected (normal left inverted right x axis y axis)
DP-1 connected 1920x1080+1920+0 (normal left inverted right x axis y axis) 510mm x 290mm
   1920x1080     60.00*+
   1680x1050     59.95  
   1280x1024     75.02    60.02  
   1152x864      75.00  
   1024x768      75.03    60.00  
   800x600       75.00    60.32  
   640x480       75.00    59.94  
   720x400       70.08 
```

lspci:

```
00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller (rev 09) (prog-if 00 [VGA controller])
    Subsystem: Hewlett-Packard Company Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller
    Flags: bus master, fast devsel, latency 0, IRQ 29
    Memory at f7800000 (64-bit, non-prefetchable) [size=4M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at f000 [size=64]
    [virtual] Expansion ROM at 000c0000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04) (prog-if 30 [XHCI])
    Subsystem: Hewlett-Packard Company 7 Series/C210 Series Chipset Family USB xHCI Host Controller
    Flags: bus master, medium devsel, latency 0, IRQ 26


```

> Did you install an update or app before it started acting strangely? Did  you change any system settings? Any coincidental power outtages or  brownouts?

Not that I can think of

---

### Post by DuckHook on 2017-02-20
> **phenomenos2 said:**
> …Not that I can think of

> **DuckHook said:**
> In System settings&#8594;Screen Display, which monitor is "Launcher placement" set at?

Please provide complete HW info. For type of info required, please see my sig: *How to Ask for Help*It is impossible to help you without proper and complete data. Please answer all original questions.

---

### Post by phenomenos2 on 2017-02-21
Apologies - I missed that question. Having now reviewed my system settings I have found a solution to the problem. Thanks for your help.

---

### Post by kennerc on 2017-02-21
You should tell how you fixed it, it would help someone facing the same issue,

---

### Post by DuckHook on 2017-02-21
> **kennerc said:**
> You should tell how you fixed it, it would help someone facing the same issue,I suspect that OP found *System settings*&#8594;*Screen Display*&#8594;*Launcher placement* pointed at wrong display. The fix would be to simply set it to the desired one.

@OP

If this is so, please confirm and then mark thread "solved" using thread tools at the top of this thread, so that others can benefit from your solution.

---

