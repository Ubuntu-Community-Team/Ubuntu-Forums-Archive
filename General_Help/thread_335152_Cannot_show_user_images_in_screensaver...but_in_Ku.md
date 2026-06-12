---
title: "Cannot show user images in screensaver...but in Kubuntu it's fine"
date: 2007-01-09
forum: General Help
---

### Post by maruchan on 2007-01-09
When I'm using Ubuntu and my screensaver starts up - for example, GLSlideshow - the screensaver displays color bars and a tv-on-fire image instead of my photos. Same goes for the desktop-distortions screensavers; instead of displaying a shot of my desktop they show color bars.

The funny thing is, this works just fine in Kubuntu on the same computer. I can see photos and all images display just fine.

Any ideas? Thanks!

---

### Post by maruchan on 2007-01-09
Interesting, the screensaver "Pictures Folder" seems to work just fine. So why wouldn't the other screensavers work? Is there some sort of timeout if it isn't able to grab an image or screenshot? This computer isn't a speed demon.

---

### Post by Bil-E-daKid on 2007-02-12
Hey there Maruchan,

Just in case you didn't find the answer to this, GLSlideShow looks in a file called .xscreensaver in your home folder - this file should have and option as follows:

imageDirectory: /path/to/your/images

Make sure the /path/to/your/images path is correct and away it'll go.  I suspect other GL screensavers will also use this

Regards
William

---

