---
title: "[SOLVED] how can I force Firefox 2 into U8.04?"
date: 2008-05-23
forum: General Help
---

### Post by curtesy on 2008-05-23
Ubuntu 8.04 installs version 3 of Firefox.  It is not acceptable to me.  I want to use Firefox 2.  The synaptic manager gleefully states that all I have to do is go to Package>force version.  I highlighted the installed Firefox 3 and went to Package, however, the force option is not available (grayed out)!  I uninstalled Firefox, however, I still do not have any option to install an earlier version, although my U7.1 does have it! What gives?  Can I modify synaptic to select another version?

---

### Post by aikiwolfie on 2008-05-23
Goto Applications > Add/Remove ... search for Firefox ... select Firefox 2 Web Browser.

---

### Post by aysiu on 2008-05-23
Try this:
[http://www.psychocats.net/ubuntu/firefox2hardy](http://www.psychocats.net/ubuntu/firefox2hardy)

P.S. Add/Remove will not let you remove Firefox 3.

---

### Post by curtesy on 2008-05-24
> **aikiwolfie said:**
> Goto Applications > Add/Remove ... search for Firefox ... select Firefox 2 Web Browser.

Add/remove per se does not exist in synaptic 8.04.  searching synaptic for firefox does show firefox 2, however, when installing that, i wind up with firefox 3 beta 5. and trying to remove firefox 3 just repeats the above.

I found firefox 2.0.0.14 on the web (a .gz file), but how do i force synaptic to load this and dump firefox 3?  or do i have to load v2 in terminal mode via sudo (in which case, how do i dump v3)?  this is a big headache and not user friendly.  U8.04 should not force firefox 3 in the installation, make it a choice.

any more ideas????

---

### Post by tom56 on 2008-05-24
In Syaptic search for the package "firefox-2" and install it. Alternatively, if you'd rather use the terminal:
```
sudo apt-get install firefox-2
```

EDIT: Aysiu did actually post the solution above. Try the page he linked to - [http://www.psychocats.net/ubuntu/firefox2hardy](http://www.psychocats.net/ubuntu/firefox2hardy)

---

### Post by curtesy on 2008-05-24
OKAY

Prob solved.  I redid the add firefox 2 sequence as originally described and also described in the web page (thank you).  The confusion stemmed from the fact that the description of firefox 2 and firefox 3 in synaptic is quite different, leading me to believe that this f 2 was an offshoot of the real f2.  the second confusion was that the launch icon remained for f3 and i did not realize that i had to create an icon for f2.

Finally i removed the f3 icon, added the f2 icon, and VOILA!  Todo esta bien.

Muchimas gracias senores (o senoras o senoritas, asi es).

ciao

Curt

---

