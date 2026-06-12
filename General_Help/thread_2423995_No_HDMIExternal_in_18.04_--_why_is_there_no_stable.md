---
title: "No HDMI/External in 18.04 -- why is there no stable fix?"
date: 2019-08-01
forum: General Help
---

### Post by spencer2 on 2019-08-01
So I've been having this ongoing problem with my external monitor working with Ubuntu these last couple weeks. I've posted several times about this but this seems to be a constant issue. Long story short: after working through gdm3, lightdm & then some in previous posts over the last couple weeks so i did a fresh reinstall over this past weekend. Things seemed to be working the last few days but then today; I turn on my laptop (Acer F15) & once again I have no external monitor & when I do the xrandr command in terminal; my HDMI is not even present at the end of the output.

Why is this suddenly such an issue? Why is there not a reliable method for ensuring that my HDMI will work?

I'm generally very patient with Ubuntu & willing to work through lots of issues: but this HDMI thing is getting stupid.

Why is this external monitor/HDMI issue still happening?

Please help: I've not even had this Ubuntu installed for a week & this is already happening again. Ubuntu: what's the problem?

---

### Post by Autodave on 2019-08-01
Are you sure that Ubuntu is causing the problem?  Have you tried another HDMI cable?  Have you tried another monitor?  Cables fail often: especially cheap ones.  Connectors in laptops get loose/worn.

---

### Post by TheFu on 2019-08-01
HDMI is controlled by the video drivers.  I see no mention of video drivers or video hardware anywhere.  I always believed that for HDMI to work, proprietary drivers were necessary.

I don't know if you are using Wayland or not, and I've avoided touching any Wayland-related stuff. Might that be connected?

I don't have 18.04, BTW.  We still use 16.04 here.

---

### Post by spencer2 on 2019-08-01
Yes: It is ubuntu. I've tried this on 2 different externals with 2 different cables. As I said, after working through multiple steps over the last couple weeks & doing a complete reinstall over the weekend; everything had been working just fine since the reinstall but then this morning back to the same issue.
No signal found per monitor & in xrandr hdmi is not even listed.

```

xrandr
Screen 0: minimum 320 x 200, current 1366 x 768, maximum 8192 x 8192
eDP-1 connected primary 1366x768+0+0 (normal left inverted right x axis y axis) 344mm x 193mm
   1366x768      60.03*+
   1360x768      59.80    59.96  
   1280x720      60.00    59.99    59.86    59.74  
   1024x768      60.04    60.00  
   960x720       60.00  
   928x696       60.05  
   896x672       60.01  
   1024x576      59.95    59.96    59.90    59.82  
   960x600       59.93    60.00  
   960x540       59.96    59.99    59.63    59.82  
   800x600       60.00    60.32    56.25  
   840x525       60.01    59.88  
   864x486       59.92    59.57  
   800x512       60.17  
   700x525       59.98  
   800x450       59.95    59.82  
   640x512       60.02  
   720x450       59.89  
   700x450       59.96    59.88  
   640x480       60.00    59.94  
   720x405       59.51    58.99  
   684x384       59.88    59.85  
   680x384       59.80    59.96  
   640x400       59.88    59.98  
   576x432       60.06  
   640x360       59.86    59.83    59.84    59.32  
   512x384       60.00  
   512x288       60.00    59.92  
   480x270       59.63    59.82  
   400x300       60.32    56.34  
   432x243       59.92    59.57  
   320x240       60.05  
   360x202       59.51    59.13  
   320x180       59.84    59.32  
DP-1 disconnected (normal left inverted right x axis y axis)
```

---

### Post by TheFu on 2019-08-01
Which video GPU drivers are being used?
[https://wiki.ubuntu.com/X/Config/HDMI](https://wiki.ubuntu.com/X/Config/HDMI)

---

