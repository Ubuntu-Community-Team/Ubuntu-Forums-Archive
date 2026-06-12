---
title: "problem changing resolution and can't change refresh rate"
date: 2006-10-27
forum: General Help
---

### Post by heande on 2006-10-27
Hello, well the problem is solved. it seems that there is a different between restarting X and rebooting the computer, anyway now it works.

/Henrik

```

Section "Monitor"
    Identifier     "Samtron96P"
    VendorName     "STN"
    ModelName      "S/T 97P/96P"
    HorizSync       30.0 - 96.0
    VertRefresh     50 - 160.0
    Modeline       "1152x864_100.00"  143.47  1152 1232 1360 1568  864 865 868 915  -HSync +Vsync
    Modeline       "1024x768_100.00"  113.31  1024 1096 1208 1392  768 769 772 814  -HSync +Vsync
    Modeline       "800x600_100.00"  68.18  800 848 936 1072  600 601 604 636  -HSync +Vsync

EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV44 [GeForce 6200 TurboCache]"
    Driver         "nvidia"
    Option "UseEDID" "False"		
 #http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION     point 10
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV44 [GeForce 6200 TurboCache]"
    Monitor        "Samtron96P"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1152x864_100.00" "1024x768_100.00" "800x600_100.00"
    EndSubSection
EndSection
```

---

