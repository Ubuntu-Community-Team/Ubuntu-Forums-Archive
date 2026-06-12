---
title: "I can't get sound to work"
date: 2007-01-14
forum: General Help
---

### Post by Magiczero on 2007-01-14
Hi 

I have big problem!  I have sound on my system!  When I right-click to ckeck the settings on the volume I see 1 speaker icon with blue & the rest have red marks through them.  My ipod works with the speakers, so I know it is **NOT ** the speakers.

Here is a screenshot of what i see!
[http://www.flickr.com/photos/tannerlynn/357614481/](http://www.flickr.com/photos/tannerlynn/357614481/) 
I hear nothing!!!

Can I get any help?
Please?
Thanks

---

### Post by scrooge_74 on 2007-01-15
You probably have somethings set to mute or very low volume.

You can try reinstalling ALSA

Edit:I see the speaker is way down

---

### Post by NeoLithium on 2007-01-15
Try doing this from terminal:
```

alsamixer

```
and turning up all the volumes in there. I know with my soundcard, something always started muted on an install; and I neeeded to turn that up before I could get anything.

---

