---
title: "Help with xrandr"
date: 2016-03-01
forum: General Help
---

### Post by nmw01223 on 2016-03-01
I am trying to work out how to use xrandr transform (14.04.4, ATI Radeon HD5450 graphics, open source driver). I have found the following:

... in other words, the device coordinates (x' y') of the transformed pixel are: 
       x' = (ax + by + c) / w'  and 
       y' = (dx + ey + f) / w', with
       w' = (gx + hy + i).

I am testing this on a VGA output (VGA-0). As a simple test it seems to me that
 ```
xrandr --output VGA-0 --transform 0.6,0,0,0,1,0,0,0,1
```
 should therefore scale the screen by squashing it to 60% of its width, but full height.

It doesn't. What actually happens is that the right 40% of the screen is black (expected), the left 60% is however just as normal, ie clipped off at 60%, not the full screen squashed into 60% (not expected).

I am clearly missing something important here, can anyone explain?

---

### Post by trag on 2016-03-08
Are you talking about overscan/underscan problems?

---

### Post by nmw01223 on 2016-03-13
> Are you talking about overscan/underscan problems?
I am, and I'm aware of properties like 'underscan', 'underscan hborder' and 'underscan vborder' which I'm having an equal lack of success with, but it is more a general question about how to get xrandr to work correctly.

---

