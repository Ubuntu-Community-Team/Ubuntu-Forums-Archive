---
title: "Hdmi cuts of borders and edges"
date: 2013-12-14
forum: General Help
---

### Post by Bill Gates Foundation on 2013-12-14
MY TV SHOULD BY 1000 LINES OF resoultion.   my nvidia says its 1024...

any ways it being cut of on the edges and i cant fix it....

  tags - cropped border, edge cut off, adjust picture size, overscan problem..


I have researched this problem and it seems to relate to an "overscan"  problem (also Nvidia no longer has a size slider in configuration panel)


I have this older TV, it says it has 1000 lines of resolution....

My NVidia 8600GT says the tv connected is 1024x768, and the edges are  always cut off...i have tried some of the tricks but none are  working....
[IMG]http://crev.vo.llnwd.net/o42/audioreview/images/products/product_123124.jpg[/IMG]

> owner@owner-945GCT-M2:~$ xrandr
Screen 0: minimum 8 x 8, current 2304 x 1024, maximum 8192 x 8192
DVI-I-0 connected primary 1280x1024+0+0 (normal left inverted right x axis y axis) 376mm x 301mm
   1280x1024      60.0*+   75.0  
   1152x864       75.0     60.0  
   1024x768       75.0     70.1     60.0  
   800x600        75.0     72.2     60.3     56.2  
   640x480        75.0     72.8     59.9  
DVI-I-1 disconnected (normal left inverted right x axis y axis)
TV-0 connected 1024x768+1280+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0*+
   800x600        60.0  
   720x480        60.0  
   640x480        60.0  
   640x400        60.0  
   512x384        60.0  
DVI-I-2 disconnected (normal left inverted right x axis y axis)
DVI-I-3 disconnected (normal left inverted right x axis y axis)
owner@owner-945GCT-M2:~$ 



> **Product Description**

53 inch Rear Projection  Television - UltraBlack Screen with Surface  Diffuser and 1000 Lines  Resolution - Digital 3D Comb Filter - 60 Watts  Audio Power - Dolby Pro  Logic Surround Sound w/ 2 Built-in Center  Speakers - Dual Tuner  Picture-in-Picture w/Dual View Split Screen - 2  Rear Audio/Video Inputs -  2 Rear S-Video Inputs - Dual RF Inputs -  Component Video Inputs -  Surround Speaker Terminals


i have tried these commands but nothing happends....

> nvidia-settings --assign 0/CurrentMetaMode="TV-0: 984x728 { ViewPortOut=904x648+60+60 }"



>  nvidia-settings --assign 0/CurrentMetaMode="DFP-1: 1024x768 { ViewPortOut=984x728+20+20 }"




I have tried many different combinations, changing around dfp and tv-0,  and changing resolution..... and seems like nothing is happening.....


There is nothing on the TV to adjust, the aspect looks best on "full"  but it doesnt matter what aspect is selected there is always something  cut off......

---

