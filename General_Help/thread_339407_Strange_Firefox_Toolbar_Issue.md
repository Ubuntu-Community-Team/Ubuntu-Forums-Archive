---
title: "Strange Firefox Toolbar Issue"
date: 2007-01-15
forum: General Help
---

### Post by gdboling on 2007-01-15
I am running Xubuntu Edgy and have been for about 2 months with no major issues.  Yesterday I noticed something odd with my Firefox toolbar.  When I hover over navigational buttons (forward, previous, home, etc) it always turns to the back arrorw.  Here is an example of what I am talking about:

[http://www.paradigmcoders.net/firefox/firefox.htm](http://www.paradigmcoders.net/firefox/firefox.htm)

I tried removing and installing FF again, but that didn't seem to fix the issue.  Anyone else seen this?

---

### Post by NeoLithium on 2007-01-15
the only thing I might suggest, is if you don't have a bunch of important bookmarks, etc; try this from terminal:
```

rm -r /home/USER/.mozilla/firefox/

```

That's where all the firefox personal settings for you are set, it would be as if you had a GENUINE first install of Firefox; and maybe that will fix it up for you.

---

### Post by gdboling on 2007-01-15
That did the trick.  Although, I probably should have checked some of my plugins first to see if one might have been causing the problem.  Especially some I had installed recently.  But all is well now. 

Thanks.

---

### Post by NeoLithium on 2007-01-15
Glad it worked out; I've had to do that more than once because of a few firefox themes and whatnot.

---

