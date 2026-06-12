---
title: "How to add 1366x768 screen resolution?"
date: 2014-10-10
forum: General Help
---

### Post by tracyone2 on 2014-10-10
use xrander

i found [http://ubuntuforums.org/showthread.php?t=1112186](http://ubuntuforums.org/showthread.php?t=1112186) 
and 
[http://ubuntuforums.org/showthread.php?t=1024907](http://ubuntuforums.org/showthread.php?t=1024907)

i already know how to add a new resolution 

but neigther of these threads can solve my problem

because I need add a resolution which is  NOT CVT COMPLIANT:1366*768@60 

so cvt or gtf command can not help me

so i need to konw the meaning of cvt command's output so that i can add a new mode according the VESA timing spec..

```


   cvt 1366 768 60
# 1368x768 59.88 Hz (CVT) hsync: 47.79 kHz; pclk: 85.25 MHz
Modeline "1368x768_60.00"   85.25  1368 1440 1576 1784  768 771 781 798 -hsync +vsync

```

i don't konw the meaning of "1440" "1576" ......

following picture is in VESA DMT spec..

[IMG]https://dl.dropbox.com/s/goexb7p10h0y4r7/vesa.jpg?dl=0[/IMG]

---

