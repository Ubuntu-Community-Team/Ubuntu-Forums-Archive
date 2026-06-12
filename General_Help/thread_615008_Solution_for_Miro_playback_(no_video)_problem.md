---
title: "Solution for Miro playback (no video) problem"
date: 2007-11-16
forum: General Help
---

### Post by briwood on 2007-11-16
I'm using gusty and just installed Miro as described here: [http://www.getmiro.com/download/ubuntu.php](http://www.getmiro.com/download/ubuntu.php)

I download a video.  When I tried to play it I got sound, but no picture.

I found [this article]("http://www.linux.com/feature/118379") that suggested editing  /usr/share/python-support/miro/miro/frontend_implementation/VideoDisplay.py to change the playback system from Xine (the default) to Gstreamer.  Here's what I did:

Exit Miro first!

```

# always make a backup
cp python-support/miro/miro/frontend_implementation/VideoDisplay.py  /usr/share/python-support/miro/miro/frontend_implementation/VideoDisplay-ORIG.py

# instead of emacs you can use 'nano' or your editor of choice
sudo emacs /usr/share/python-support/miro/miro/frontend_implementation/VideoDisplay.py

```

I edited lines 77-78 so they read as follows:
```

            self.add_renderer("gstrenderer")
            #self.add_renderer("xinerenderer")

```

Then I started Miro and was able to play my video.

(Perhaps updating Xine is another way to fix this.)

Enjoy.  Now I really don't have to buy a TV!

---

### Post by Anduu on 2007-11-16
Thanks for the heads up...Ive been meaning to take another look at Miro...Now Ill know what to try if that happens :KS

---

### Post by Ace_NoOne on 2008-03-16
Thanks, that did indeed solve this problem for me.
However, I'd much rather use an external video player (e.g. SMPlayer)...

---

