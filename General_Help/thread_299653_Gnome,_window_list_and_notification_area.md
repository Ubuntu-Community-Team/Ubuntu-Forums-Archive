---
title: "Gnome, window list and notification area"
date: 2006-11-14
forum: General Help
---

### Post by hoagie on 2006-11-14
My panel is transparent, I changed it from it's properties, but every applet, or window list, notification bar I add on  it, comes with a white background, which doesn't look nice. Please help me sort this out.

Thank you, Hoagie

[IMG]http://www.flickr.com/photo_zoom.gne?id=297479851&size=o[/IMG]

---

### Post by justinjstark on 2006-11-14
> **hoagie said:**
> My panel is transparent, I changed it from it's properties, but every applet, or window list, notification bar I add on  it, comes with a white background, which doesn't look nice. Please help me sort this out.

Thank you, Hoagie

[IMG]http://www.flickr.com/photo_zoom.gne?id=297479851&size=o[/IMG]

Yep, that's actually fairly normal.  It has to do with gnome-panel using pseudo-transparency and the panel applets setting their backgrounds to the system background color (which is white).

There's really no way to fix this that I am aware of.  You can try enabling real transparency using beryl:
[http://doc.gwos.org/index.php/BerylOnEdgy](http://doc.gwos.org/index.php/BerylOnEdgy)
which will allow you to set the transparency of panels, however, the panel content will also become transparent (buttons, applets, etc) which is probably not what you want.

PS: Your image is not showing up.  It would be better to link to it than to use the IMG tag.

---

### Post by hoagie on 2006-11-14
That's what I thought at first, but how come this be true then ?
[http://ubuntuforums.org/gallery/showphoto.php?photo=3886&size=big&cat=](http://ubuntuforums.org/gallery/showphoto.php?photo=3886&size=big&cat=)

---

### Post by justinjstark on 2006-11-14
Hmmm...ya, now I see what you mean.  And I don't really have an answer.  If I were you I would just play around with removing/adding applets and moving them around to see if maybe it's just a kink.  Other than that I guess I'm not much help.

---

### Post by hoagie on 2006-11-14
Fixed it. I changed the controls theme, and everything worked. I noticed that some themes keep the applets white and others don't.

---

