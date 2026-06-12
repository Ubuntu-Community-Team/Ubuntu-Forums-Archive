---
title: "Problem with Xrandr 1.2 utility"
date: 2008-06-05
forum: General Help
---

### Post by madhi6.2 on 2008-06-05
I have Xrandr 1.2 version, when I give Xrandr -q or xrand -query
I get following output::::

# xrandr --query
 SZ:    Pixels          Physical       Refresh
*0   1600 x 1200   ( 310mm x 231mm )  *69   68   67
 1   1280 x 1024   ( 310mm x 231mm )   80   79   78
 2   1024 x 768    ( 310mm x 231mm )   105  104  103
 3    800 x 600    ( 310mm x 231mm )   133  132  131
 4   1400 x 1050   ( 310mm x 231mm )   75   60
 5   1280 x 960    ( 310mm x 231mm )   85   60
 6   1152 x 864    ( 310mm x 231mm )   75
 7   1152 x 768    ( 310mm x 231mm )   55
 8    928 x 696    ( 310mm x 231mm )   60
 9    896 x 672    ( 310mm x 231mm )   60
 10   832 x 624    ( 310mm x 231mm )   75
 11   700 x 525    ( 310mm x 231mm )   75   60
 12   640 x 512    ( 310mm x 231mm )   75   60
 13   640 x 480    ( 310mm x 231mm )   85   75   73   60
 14   720 x 400    ( 310mm x 231mm )   85
 15   640 x 400    ( 310mm x 231mm )   85
 16   576 x 432    ( 310mm x 231mm )   75
 17   640 x 350    ( 310mm x 231mm )   85
 18   576 x 384    ( 310mm x 231mm )   55
 19   512 x 384    ( 310mm x 231mm )   85   75   70   60   87
 20   416 x 312    ( 310mm x 231mm )   75
 21   400 x 300    ( 310mm x 231mm )   85   75   72   60   56
 22   320 x 240    ( 310mm x 231mm )   85   75   73   60
 23   360 x 200    ( 310mm x 231mm )   85
 24   320 x 200    ( 310mm x 231mm )   85
 25   320 x 175    ( 310mm x 231mm )   85
Current rotation - normal
Current reflection - none
Rotations possible - normal
Reflections possible - none


Thus, I am unable to know which mode is currently connected(i.e VGA, LVSD, DVI etc.)

Basically I want to simulate turning on and off of my Monitor.

I am doing
 $ xrandr –output VGA-0 –off

but, its not working.

Any help in this respect is greatly appreciated.

---

