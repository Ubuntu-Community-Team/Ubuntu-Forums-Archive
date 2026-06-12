---
title: "Firefox will not allow upgrades in Hoary"
date: 2008-05-11
forum: General Help
---

### Post by BoredOutOfMyMind on 2008-05-11
I found many addons and skins will not work in FF 3.0.  So I found FF2 in Synaptic and installed that.  Ok, better, except now any themes and addons will not install. 

How do I purge FF 3.0 off Hoary and revert to FF 2 so I can have this the way I was used to before?  I miss Adblock and craigslist preview most of all. :mad:

---

### Post by BoredOutOfMyMind on 2008-05-11
Anyone who has the same problems in FF?

---

### Post by ghost_ryder35 on 2008-05-11
the answer to downgrading to ff2.0 is here [http://ubuntuforums.org/showthread.php?t=773851](http://ubuntuforums.org/showthread.php?t=773851)

---

### Post by latna on 2008-05-11
Ok I've been meaning to get around to this and you've inspired me to actually figure it out.

What I did was create a new profile with:

```
firefox -ProfileManager
```

I named the new profile Version2, then unchecked the box that says "don't ask me at startup". Now when I start firefox-2 or firefox-3.0, it asks me which profile to use. Of course you have to copy any files you need such as bookmards over to the new profile.

P.S. You could also just highlight the profile you want and leave "don't ask me at startup" checked if you'll only be using firefox-2.

HTH

---

### Post by BoredOutOfMyMind on 2008-05-11
> **ghost_ryder35 said:**
> the answer to downgrading to ff2.0 is here [http://ubuntuforums.org/showthread.php?t=773851](http://ubuntuforums.org/showthread.php?t=773851)

Thank you!

I searched for it, I KNEW it HAD to be here if it happenned to me here. 

It is actually this thread-

[http://ubuntuforums.org/showthread.php?t=784628](http://ubuntuforums.org/showthread.php?t=784628)

:)

Oh, and I love that Dog in your avatar!

---

### Post by Woody1987 on 2008-05-11
Im just curious as to whether you meant hardy, and not hoary, because hoary is quite old now.

---

### Post by BoredOutOfMyMind on 2008-05-11
> **Woody1987 said:**
> Im just curious as to whether you meant hardy, and not hoary, because hoary is quite old now.

Maybe THAT is why I did not get a swift response!

:lolflag:

---

