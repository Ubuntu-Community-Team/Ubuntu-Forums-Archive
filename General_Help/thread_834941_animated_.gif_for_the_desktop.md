---
title: "animated .gif for the desktop?"
date: 2008-06-20
forum: General Help
---

### Post by ucal on 2008-06-20
Is it possible to have an animated .gif as the background actually be animated?  This would be an amazing feature.

---

### Post by Fingers &amp; Thumbs on 2008-06-20
There is a utility called xwinwrap, which will allow you to do this, unfortunately, you have to sacrifice the functionalality of your desktop (No Icons/folders or mounted media wil show, and no right click context menu etc).

   It was 6 months ago when I tried this, and at the time I found no other solution, however at the suprising rate things develop in linuxland, it's possible that this has been fixed. Try Googling "ubuntu animated wallpaper"

---

### Post by ucal on 2008-06-20
Thanks.  That isn't exactly what I want, but hopefully the programming scene has added some more solutions.

---

### Post by attari on 2008-06-20
> **ucal said:**
> Is it possible to have an animated .gif as the background actually be animated?  This would be an amazing feature.


You can have animated gif, SWF and movie files as wallpaper in KDE but not in Gnome. Google for info on how to do so.

---

### Post by ucal on 2008-06-20
After doing some research, I believe it is possible, but it would require a .png (or any other .image file) for every slide.  This is accomplished through the use of xml scripts.  I'm running one right now, but it switches the image after a few hours, not miliseconds. 

The plus side of this method is that folder icon functionality is maintained.  The downside is that it isn't very user friendly.  I don't know the basics of script writing, so I'm going to have to figure it out before I make my own.

---

### Post by cor2y on 2008-06-20
In the latest gnome you can have a slide show of wallpapers, with slow overlay transitions at a specific time or every few seconds.
Like the mac folks have.
Its a new implementation so theres no gui from which you can do it but you can create a xml file for it.
See this post.
[http://ubuntuforums.org/showpost.php?p=4992430&postcount=4](http://ubuntuforums.org/showpost.php?p=4992430&postcount=4)
Or this thread
[http://ubuntuforums.org/showthread.php?t=784881](http://ubuntuforums.org/showthread.php?t=784881)
The downside is if you do it yourself you will need to manualy add the specific image files and make sure no mistakes in syntax ,if you create your own custom xml file, were made, so far tried all three examples and the they work.

---

### Post by Cresho on 2008-06-23
[http://www.gnome-look.org/content/show.php/All+Day+Long+(Animated+Wallpaper)?content=83443](http://www.gnome-look.org/content/show.php/All+Day+Long+(Animated+Wallpaper)?content=83443)

mines changes color according to day time.  you can also make jpg animate.  just follow the discussion:popcorn:

---

### Post by hybrazil on 2008-08-06
> **cor2y said:**
> In the latest gnome you can have a slide show of wallpapers, with slow overlay transitions at a specific time or every few seconds. Like the mac folks have.

I think there's a package called Drapes that does this (rotating the background, not displaying animated gifs). You should be able to access it in the universe. Having said that, I know that package worked nicely under earlier versions of Ubuntu, such as Dapper, but I think it might be a bit touch and go with the newer versions with the newer screen effects.

---

