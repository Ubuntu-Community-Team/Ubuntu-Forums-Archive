---
title: "No Graphics Driver -- incorret max resolution, Compiz overuses CPU"
date: 2013-09-12
forum: General Help
---

### Post by Utnubu42 on 2013-09-12
I recently installed Ubuntu 13.04 on my computer (Toshiba Portege  R835-P80x), and I have had problems ever since. My screen resolution  cannot be set above 1280x768 when the correct resolution should be  1366x768 -- increasing the max resolution using  [http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html](http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html)  and didn't help. Also, Compiz routinely takes up around 30% of CPU  usage when I perform actions like moving windows around.

I suspected my graphics driver was not working, and this seems to be the case.

The output of xrandr is:
```
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 1280 x 720, maximum 1280 x 768
default connected 1280x720+0+0 0mm x 0mm
   1280x720        0.0* 
   1024x768       61.0  
   800x600        61.0  
   640x480        60.0  
   1280x768        0.0
```

The output of lspci | grep VGA is:
```
00:02.0 VGA compatible controller: Intel Corporation 2nd  Generation Core Processor Family Integrated Graphics Controller (rev  09)
```

The output of sudo lshw -c video is:
```
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller cap_list
       configuration: latency=0
       resources: memory:c0000000-c03fffff memory:b0000000-bfffffff ioport:3000(size=64)
```

What can I do to get my graphics card working?

---

### Post by Utnubu42 on 2013-09-15
Bump. My computer is not usable because of this problem. The screen is blurry and even switching workplaces has a big lag. Any help would be greatly appreciated!

---

