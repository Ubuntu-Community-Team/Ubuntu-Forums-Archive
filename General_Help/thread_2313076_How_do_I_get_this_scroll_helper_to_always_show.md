---
title: "How do I get this scroll helper to always show?"
date: 2016-02-09
forum: General Help
---

### Post by ardchoille422 on 2016-02-09
I've noticed that in some of my apps there is a rectangle that appears near the scrollbar to aid in scrolling (the rectangle has up/down arrows on it), but some apps don't app to have this item. It shows in the dash (apps list) and in Xchat, but not in Nautilus.

Screenshot:
[ATTACH=CONFIG]267212[/ATTACH]

 I think this is part of the overlay scrollbar and I find it really helpful.

My question:
How do I get this rectangle to show in all apps?

My system:
64 bit laptop
Ubuntu 15.10 (Wily) running the Unity desktop

---

### Post by QDR06VV9 on 2016-02-09
Sorry but Overlay bars mean that they will show only when your mouse is over the border. 
Maybe a request to the Devs..
Oh and there is this [Ubuntu 15.10 Ditches Unity Overlay Scrollbars]("http://www.omgubuntu.co.uk/2015/08/ubuntu-15-10-drops-unity-overlay-scrollbars")
> [COLOR=#000000](edit: the screenshot didn't seem to post, I used drag & drop. screenshots are only allowed via url?)[/COLOR]
Yes a URL or attach a screenshot via the paperclip in the tools advanced, and resize big files to help others with bandwidth limits or visual impairments. 
Kind regards

---

### Post by ardchoille422 on 2016-02-09
> **runrickus said:**
> Sorry but Overlay bars mean that they will show only when your mouse is over the border. 
Maybe a request to the Devs..
Oh and there is this [Ubuntu 15.10 Ditches Unity Overlay Scrollbars]("http://www.omgubuntu.co.uk/2015/08/ubuntu-15-10-drops-unity-overlay-scrollbars")

Yes a URL or attach a screenshot via the paperclip in the tools advanced, and resize big files to help others with bandwidth limits or visual impairments. 
Kind regards

My question was: How do I get this to **show in all apps**? See the rectangle outlined in red, next to the red arrow. That little rectangle with the arrows on it, that is what I want to show in the scrollbar in all apps. I find it very useful.

[ATTACH=CONFIG]267210[/ATTACH]

---

### Post by QDR06VV9 on 2016-02-09
I knew what you meant...
See this [https://askubuntu.com/questions/35770/enable-overlay-scrollbars-in-all-applications](https://askubuntu.com/questions/35770/enable-overlay-scrollbars-in-all-applications)
If you are using an older release there was this [http://www.webupd8.org/2011/03/set-all-applications-to-use-overlay.html](http://www.webupd8.org/2011/03/set-all-applications-to-use-overlay.html)
But that is all I can offer ATM

---

### Post by ardchoille422 on 2016-02-09
> **runrickus said:**
> I knew what you meant...
See this [https://askubuntu.com/questions/35770/enable-overlay-scrollbars-in-all-applications](https://askubuntu.com/questions/35770/enable-overlay-scrollbars-in-all-applications)
If you are using an older release there was this [http://www.webupd8.org/2011/03/set-all-applications-to-use-overlay.html](http://www.webupd8.org/2011/03/set-all-applications-to-use-overlay.html)
But that is all I can offer ATM

Ok, it looks like this isn't possible. I find it inconsistent that one app has this item and others lack it.

Thank you for your help.

---

### Post by Geoffrey_Arndt on 2016-03-21
Ubuntu is discontinuing that tyhpe of marker (rectangle) . . . and moving to the standard Gnome scroller (back to traditional method).

---

### Post by vasa1 on 2016-03-22
> **Geoffrey_Arndt said:**
> Ubuntu is discontinuing that type of marker (rectangle) . . . and moving to the standard Gnome scroller (back to traditional method).On a lighter note, I believe there isn't anything like a standard GNOME scroller ;)

As for OP's comment > Ok, it looks like this isn't possible. I find it inconsistent that one app has this item and others lack it. 
There's the GTK2/GTK3 divide. 

Then there are qt4/qt5 apps which can be made to look somewhat GTK-like.

Then there's the fact that "Linux" isn't Apple. Application developers have considerable leeway (freedom?). I sense a trend to tame the Wild West using "brand-recognition" or "integrated experience" arguments. Let's see how that develops.

---

### Post by vasa1 on 2016-03-22
In later versions of Ubuntu, the scrollbars of gtk3 apps will be "different" in more ways than one. You can see that in gtk3 apps if you run a live USB of 16.04. 

Fortunately, there's a fix for one feature and that's described by Toz here: [https://forum.xfce.org/viewtopic.php?pid=37175#p37175](https://forum.xfce.org/viewtopic.php?pid=37175#p37175)

For the other feature, one can add *gtk-primary-button-warps-slider=false* to one's ~/.config/gtk-3.0/settings.ini.

---

