---
title: "Ubuntu 18 &amp; Thinkpad Dock - External Monitor available rate not working"
date: 2020-04-04
forum: General Help
---

### Post by rob67 on 2020-04-04
Running Ubuntu 18, on a Thinkpad E590, connected to a Thinkpad USB-C  Dock, which is then connected, via DisplayPort to an Ultrawide monitor.
  This monitor's native resolution is 3840x1600 @ 60hz.
  This set up works perfectly fine in Windows 10; I get the resolution and I get the refresh rate of 60.
  In Ubuntu, I can only get the external monitor to run at 29.99hz, even though 59.99 is an available option in xrandr:
  Output of xrandr:
  ```
DP-1-2 connected 3840x1600+1920+0 (normal left inverted right x axis y axis) 874mm x 366mm
   3840x1600     59.99 +  29.99* 
   3440x1440     75.05    59.97  
   2560x1080     50.00  
   1920x1080     74.99    60.00    60.00    50.00    59.94  
   1680x1050     59.95  
   1600x900      60.00  
   1280x1024     75.02    60.02  
   1280x800      59.81  
   1152x864      75.00    59.97  
   1280x720      60.00    50.00    59.94  
   1024x768      75.03    60.00  
   832x624       74.55  
   800x600       75.00    60.32  
   720x576       50.00  
   720x480       60.00    59.94  
   640x480       75.00    60.00    59.94  

```  So you can see 59.99 is reported as an available rate, but...
  ```
xrandr --output DP-1-2 --mode 3840x1600 --rate 59.99

```  doesn't change the rate; it stays on 29.99 and reports:
  ```
xrandr: Configure crtc 1 failed

```  xorg.log shows:
  ```
4395.610] (EE) modeset(0): failed to set mode: No space left on device
[  4398.303] (II) modeset(0): EDID vendor "LEN", prod id 16570
[  4398.303] (II) modeset(0): Printing DDC gathered Modelines:
[  4398.303] (II) modeset(0): Modeline "1920x1080"x0.0  138.60  1920 1968 2000 2080  1080 1083 1088 1111 -hsync -vsync (66.6 kHz eP)
[  4398.303] (II) modeset(0): Modeline "1920x1080"x0.0  110.88  1920 1968 2000 2080  1080 1083 1088 1111 -hsync -vsync (53.3 kHz e)

```  I would accept that the 59.99 isn't supported if it didn't show in xrandr... but it does!
  I have updated the Thinkpad dock to the latest firmware, and also installed the latest DisplayLink drivers from [https://www.displaylink.com/downloads/ubuntu](https://www.displaylink.com/downloads/ubuntu)
  Also, after initial setup, I experienced screen flickering with the dock, so disabled PageFlip as per [https://support.displaylink.com/knowledgebase/articles/1181623-displaylink-ubuntu-driver-after-recent-x-upgrades](https://support.displaylink.com/knowledgebase/articles/1181623-displaylink-ubuntu-driver-after-recent-x-upgrades)
  Any suggestions, most appreciated.
  Thanks

---

