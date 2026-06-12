---
title: "console refresh rate"
date: 2008-05-29
forum: General Help
---

### Post by samrat1985 on 2008-05-29
could specify on how to change "console refresh rate" 
using fbset @ boot time. I am using vesa 'VGA=786' parameter.
vesa framebuffer and fbset shows 640x480@75. I want to change it
to 640x480@85 
ubuntu 7.04 @ nvidia 6200

---

### Post by alienexplorers on 2008-06-03
You could try adding a modeline to your monitor section of xorg.conf....  You can generate a modeline by using:
> terminator@terminator-desktop:/etc/apt$ gtf 1024 768 70

  # 1024x768 @ 70.00 Hz (GTF) hsync: 56.00 kHz; pclk: 76.16 MHz
  Modeline "1024x768_70.00"  76.16  1024 1080 1192 1360  768 769 772 800  -HSync +Vsync

You would then add the modeline as shown below:
> Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Delta"
    HorizSync       31.0 - 68.0  <---- adjust to your monitors Horizontal Syync Rate
    VertRefresh     56.0 - 85.0  <---- adjust to your monitors Verticle Refresh Rate
    Option         "DPMS"
    ModeLine       "1280x768_70.00" 95.0 1280 1352 1488 1696 768 769 772 800 -hsync +vsync
EndSection


---

### Post by samrat1985 on 2008-07-12
Thanks I will try that out :)

---

