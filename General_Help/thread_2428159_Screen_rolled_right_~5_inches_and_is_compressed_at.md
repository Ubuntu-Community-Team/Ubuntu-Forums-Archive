---
title: "Screen rolled right ~5 inches and is compressed at bottom"
date: 2019-09-30
forum: General Help
---

### Post by jinga on 2019-09-30
I've installed xubutu 18.04 on my Toshiba Satellite P25-S5263 32bit laptop and encountered a problem where the screen is rolled right ~5” and is compressed at the bottom with the top of the display duplicated at the bottom. The graphics application indicates 1024x768 and any other selections make things worse.


---


I’ve tried setting up /etc/X11/xorg.conf and it is ignored and it defaults to the rolled screen:
Section "Monitor"
  Identifier "Configured Monitor"
  Option "DPMS"    "true"
  HorizSync    30.0-60.0
  VertRefresh    50.0-70.0
EndSection


Section "Screen"
  Identifier "Default Screen"
  Monitor "Configured Monitor"
  Device "Configured Video Device"
  DefaultDepth    24
  Subsection "Display"
    Depth 24
    Modes "800x600" "1024x768" "1280x1024" "1440x900"
  EndSubSection
EndSection


---


xrandr output when screen is rolled to right:
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 4096 x 4096
LVDS-1 connected primary 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768      60.00*+
   800x600       59.96  
   640x480       59.94  
   720x400       59.97  
   640x400       59.96  
   640x350       59.84  
VGA-1 disconnected (normal left inverted right x axis y axis)
TV-1 disconnected (normal left inverted right x axis y axis)


---


I then tried “dropping to root shell” by “holding shift at startup”, selecting “Advanced Options for Ubuntu”, “Ubuntu, with Linux 4.15.0-64-generic (recovery mode)”, “resume” and “OK”  The monitor displays correctly for a 1024x768 monitor with no rolling.


xrandr output after starting in recovery mode:
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768      61.00* 
   800x600       61.00  
   640x480       60.00  


---


TheNVIDIA GeForce FX Go5200 graphics controller supports:
800x600        60/70/72/75/85/100/120HZ
1024x768    60/70/72/75/85/100/120HZ
1280x1024    60/70/72/75/85/100/120HZ
1440x900    60/70/72/75/85/100HZ
1600x1200    60/70/72/75/85/100HZ
1680x1050    60/70/72/75/85/100HZ
1920x1200    60HZ
1920x1440    60HZ
2048x1536    60HZ


The 17" wide XGA TFT active matrix display supports upto 16M colors at 1440x900


---


I would like to find a way to use a higher resolution and also be able to boot normally.

---

