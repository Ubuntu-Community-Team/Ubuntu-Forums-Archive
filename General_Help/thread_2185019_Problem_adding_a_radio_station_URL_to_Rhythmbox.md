---
title: "Problem adding a radio station URL to Rhythmbox"
date: 2013-10-31
forum: General Help
---

### Post by mithen2 on 2013-10-31
(Ubuntu 12.04 LTS 32bit)

This is my favorite radio station but Rhythmbox won't accept this URL:

[URL="http://radioplayer.magic.co.uk/live/"]
http://radioplayer.magic.co.uk/live/[/URL]

  A different radio station URL that works is:

[URL="http://www.bbc.co.uk/radio/listen/live/r5l.asx"]
http://www.bbc.co.uk/radio/listen/live/r5l.asx[/URL]

  On the magic website I couldn't find a copy URL option. What's the solution to this problem? :|

---

### Post by kostkon on 2013-10-31
I checked the page's source and found out that they provide a url for their html5 fallback player that loads when Flash is not available, i'm guessing, so try adding the following url in Rhythmbox, it should play fine
```
http://tx.whatson.com/icecast.php?i=magic1054low.mp3
```

Hope that helps.

---

