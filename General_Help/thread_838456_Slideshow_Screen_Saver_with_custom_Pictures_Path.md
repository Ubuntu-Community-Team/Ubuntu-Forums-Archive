---
title: "Slideshow Screen Saver with custom Pictures Path"
date: 2008-06-23
forum: General Help
---

### Post by Harry Muscle on 2008-06-23
I noticed that the screen savers don't have any options, etc. and apparently this is by design.  I was therefore wondering if anyone could help me figure out how to setup a screen saver that plays pictures (ie: Slide Show) and points to a custom path (network path to be specific).  Hopefully it's just a matter of editing a setup file for one of the build in screen savers that does slide shows.

Thanks,
Harry

---

### Post by Harry Muscle on 2008-06-23
OK, I figured out that you have to change the personal-slideshow.desktop file and add a --location argument to the exec line, however, I tried adding a path to my network location, but I'm guessing I'm messing up on that part.  Could someone tell me how I would point the screen saver to the following location:

Server\Media\Pictures

Server is the machine name
Media is the share name
Pictures is a folder on that share

Thanks,
Harry

---

### Post by stingray_17 on 2008-12-16
I tried installing "xscreensaver" and, what do you know -- it created a second Screensaver Preferences option on my menu with an "Advanced" tab which allows me to change the location of the images.

---

### Post by puppe on 2011-06-29
I added the --location argument to my slideshow.desktop file and it worked fine. (for my local picture folder)
Thanks for the tip.

---

