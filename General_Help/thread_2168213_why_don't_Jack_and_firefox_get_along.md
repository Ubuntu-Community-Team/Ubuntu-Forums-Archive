---
title: "why don't Jack and firefox get along"
date: 2013-08-16
forum: General Help
---

### Post by chkneater on 2013-08-16
I have all the updated Firefox and Jack libs.  I don't understand why when running jack, firefox locks up continually, doesn't want to open pages, and flashplayer either won't play or will freeze everything?  I run jack a lot, and I search and use the web a lot, see, I have this thing called email that needs checking, and I can't quit Jack just to check email or look something up.  This is frequent and annoying.  Wherer is the Jack plugin for Firefox??????!!!!!!!

---

### Post by CatKiller on 2013-08-17
The problem is Flash and its assumption of OSS. ISTR that you could define a default output in ALSA's conf file that kept Flash happy and let it turn up as just another audio source in JACK, but I can't remember the details at the moment.

---

### Post by chkneater on 2013-08-17
Hmmm... well that's something at least I can go on... also makes sense that flash would eat up OSS too...  If you can remember that line let me know, thanks!!!

---

### Post by CatKiller on 2013-08-18
I think it might have been the first link on[ this page]("http://jackaudio.org/routing_flash") that I was vaguely remembering, but the text on the page itself is interesting, too. I don't even have Flash installed any more, which is why I can't be more helpful.

---

### Post by Yellow Pasque on 2013-08-19
No, Flash doesn't use OSS without a special library. Flash uses ALSA's lib (libasound). On modern systems, programs using libasound get routed to pulseaudio via the asound-pulse plugin (in libasound2-plugins package). You may need to find some way to route asound through jack without screwing up the rest of your sound. You may find this helpful: [http://jackaudio.org/routing_alsa](http://jackaudio.org/routing_alsa)

---

