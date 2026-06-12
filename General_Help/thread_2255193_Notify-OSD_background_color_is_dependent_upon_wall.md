---
title: "Notify-OSD background color is dependent upon wallpaper color. Can I change that?"
date: 2014-12-02
forum: General Help
---

### Post by Roasted on 2014-12-02
It seems as if notify-osd's color choices is based on your wallpaper. This is wildly frustrating for me, as I have a black and white picture of my daughter as my wallpaper. As such, the gray background to notify-osd notifications is rather bright, yet it retains white text. I'd like to know if there's a way to break that connection so I can have legible notifications (i.e. white text on dark dark gray or black) while retaining my wallpaper.

Note: I know about the customizable notify-osd PPA. I'm trying to avoid using that, mostly because I refuse to believe that I'll need a 3rd party PPA to fix this madness. Though if all other options are exhausted, I'll give it a shot.

For those curious, in terminal run notify-osd send "test". After that, change your wallpaper to something with an obvious color change, then run notify-osd send "test" again. You'll see what I mean.

Any ideas?

---

### Post by mc4man on 2014-12-03
It's very simple- 
You want to further configure notify-osd then either use the ppa or edit the source yourself. 
Case closed. 
(the newer version in ppa will default to the Dash color which is configurable in ccsm. otherwise ~/.notify-osd is the place

---

### Post by vasa1 on 2014-12-03
[http://ubuntuforums.org/showthread.php?t=2245490](http://ubuntuforums.org/showthread.php?t=2245490)

---

### Post by Roasted on 2014-12-03
> **mc4man said:**
> It's very simple- 
You want to further configure notify-osd then either use the ppa or edit the source yourself. 
Case closed. 
(the newer version in ppa will default to the Dash color which is configurable in ccsm. otherwise ~/.notify-osd is the place

I figured as such. It just seems like a foolish design choice to be notify-osd background based on wallpaper (something that you see so rarely), as opposed to the coloring/background of say the left panel or the top panel. That would make far more sense and make for greater consistency.

> **vasa1 said:**
> [http://ubuntuforums.org/showthread.php?t=2245490](http://ubuntuforums.org/showthread.php?t=2245490)

Ahh yes, this is coming back to me now. I remember striking out with the xfce notifications for some reason... perhaps I'll just PPA it up and be done with it. Kind of frustrating a PPA is needed to take care of a half baked hard coded design choice, but oh well. Could be worse, I suppose.

Thanks everyone.

---

