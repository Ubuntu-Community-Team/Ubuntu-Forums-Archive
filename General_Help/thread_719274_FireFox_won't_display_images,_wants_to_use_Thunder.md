---
title: "FireFox won't display images, wants to use Thunderbird"
date: 2008-03-09
forum: General Help
---

### Post by eternicode on 2008-03-09
I really could've sworn that this was a common problem, and one that I've seen adressed many times, but no amount of searching has turned up an answer.

Firefox, when asked to "view image" or "view background image", will randomly act as if it's downloading the image, and wants to use Thunderbird as the default handler.  I don't understand why Thunderbird, but I want FireFox or, at the least, Gwenview, to handle the file.

Right at the moment, if I go to [http://woork.blogspot.com/](http://woork.blogspot.com/) and "right-click" -> "view background image" on the "# comments", it'll try to download the PNG file.  On another site, [http://www.smashingmagazine.com/](http://www.smashingmagazine.com/) , viewing the background of the side-shaded sidebar works perfect.

I checked out a couple more blogger sites, and it seems to have issue with only the blogger-hosted images.  Other images from other sites work fine.  Does anyone know how to change the default handler for these instances or, better yet, how to make FireFox automatically handle ALL image files?  I'm guessing the issue is some google setting that sends a download header...

Using FF 2.0.0.12.

---

### Post by erginemr on 2008-03-10
As a work-around to this problem, you can instruct Firefox how it will open the images. When you right click the image, a dialog box will pop-up and you can select whichever application you desire pictures to open with. You can even point to "/usr/share/bin/firefox" to let Firefox show the image.

I think this relates to how the page has been designed in [http://woork.blogspot.com/](http://woork.blogspot.com/), because this doesn't happen in, say [http://www.ubuntu.com/](http://www.ubuntu.com/). There, Firefox acts as expected, when you right-click the ubuntu logo with the lying people background and select "view background image".

Alternatively, you may want to have a look at Firefox Menu -> Edit -> Preferences -> Content -> Button with the title "Manage...", where you will probably see a customized action for JPG/PNG images with Thunderbird as the main actor. You can delete this line to let Firefox return to its default behavior.

---

