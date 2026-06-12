---
title: "FavIcon Reloader 0.8 with Firefox 38"
date: 2015-05-22
forum: General Help
---

### Post by mdavis1231 on 2015-05-22
I was using this to load all of my bookmark favicons before I had to unfortunately reinstall my Ubuntu 14.04 LTS a few days ago.  Now all of a sudden, all I'm getting is the options box, and there doesn't seem to be any way to access the screen that actually loads the favicons.  Anybody else using FavIcon Reloader 0.8 and having this same problem?

---

### Post by Knocks on 2015-08-16
I was having this issue, but only with a few out of 200+ bookmarks that I had.  I tried everything, but those 3 or 4 sites were still showing blank favicons.  It turned out to be a server side issue (these sites were on my company WAN).  I re-created the missing favicons with a [favicon generator]("http://www.favicongenerator.com") and re-uploaded them to the server, then refreshed Favicon Reloader's bookmark cache, and everything started working.

---

