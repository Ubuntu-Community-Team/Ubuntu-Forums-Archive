---
title: "Mousewheel adjustments"
date: 2007-03-23
forum: General Help
---

### Post by kc0eks on 2007-03-23
Hey everyone,

Thanks for your help..before hand ;)

Being quite new to ubuntu just getting my mouse buttons working was a bit of a challenge, now I would like to fix something else..

I have a MS laser mouse 6000 (I know...its MS on linux..hah)

Anyway the scroll wheel works but is very touchy and jumpy, i cant scroll a little at a time, as i usually jump all over the place and scroll right past what I wanted to look at. 

I sort of fixed this in firefox with the smoothscroll extension but I would like to fix it for all apps.

I imagine i need to add/modify xorg.conf or something but I cant seem to find any setting I might add.

Thanks all!

---

### Post by 1/0 on 2007-03-23
Interesting question. I Know that the mouse speed is set either in xorg.conf or in terminal by:
```
xset m 5 10
```

But the scroll speed is not set that way. I think the mouse scroll speed is set by xorg but its probably overridden by gconf. I guess you should try some settings in xorg. These are commands that are interesting but I don't remember exactly how they affected the scrolling speed. You'll have to google that.

```
Option "VertScrollDelta" "25"
Option "HorizScrollDelta" "25"
Option "CoastingSpeed" "3.0"
```

I read somewhere that Microsoft has a built in hardware control of their mice. It could be the built in scroll acceleration that creates the problem. Maybe that's why Linux can't control the mouse the regular way. In that case you'll need to turn it off and the only way to do that is by using Microsoft's own corporate owned mouse driver, i.e. you'll have to turn it of via Windows...

Hope it helps

---

### Post by kc0eks on 2007-03-25
I appreciate your help...I will give those options a shot.

I really wish my last run with logitech mice didnt wind up so bad...they just sucked so terribly bad I took them back and went with an MS mouse which I have never done... hah.

---

