---
title: "Strange Compiz Behaviour"
date: 2006-07-30
forum: General Help
---

### Post by BitTorrentBuddha on 2006-07-30
Hi, I just installed 6 weeks of updates, and now Compiz is acting strange, my windows key isn't recognized at all (set to meta in keyboard settings, use to have <Mod4>R to run application and several other hotkeys using it.) Also when I move my cursor off to one of the corners it does the F12 window selector or the F11 window seletor (depending on which corner.) How would I fix my shortcuts (changing them in gconf-editor under apps->compiz->general->allscreens->options didn't do it,) and how would I stop the cursor in the corner from initiating the window selector?

PS is there a working equivalent of Compiz Tools?

---

### Post by WakkiTabakki on 2006-07-30
Hi
Do you start compiz through:
compiz --replace gconf

In this case, changing the shortcuts in gconf-editor *should* work.
Try installing gset-compiz, it worked for me.

Otherwise, try the forum at [www.compiz.net](www.compiz.net)

/N

---

### Post by BitTorrentBuddha on 2006-07-30
Thanks for the response, I noticed that I need to set the shortcuts to *_key not just *, it's different from the version of compiz I was running 6 weeks ago, but [this](http://en.opensuse.org/Compiz) guide was a HUGE help for me.

---

