---
title: "Why is Kubuntu using all my RAM?"
date: 2007-10-29
forum: General Help
---

### Post by bimmerd00d on 2007-10-29
Somehow ALL 4GB of my machine is being used by all the apps.  Firefox using 500mb?  What's going on here?  It didn't do this under Gnome, my laptop doesn't use all 2GB of RAM.

---

### Post by aysiu on 2007-10-29
> **bimmerd00d said:**
> Somehow ALL 4GB of my machine is being used by all the apps.  Firefox using 500mb?  What's going on here?  It didn't do this under Gnome, my laptop doesn't use all 2GB of RAM.
Unused RAM is wasted RAM. Read more here:
[http://gentoo-wiki.com/FAQ_Linux_Memory_Management](http://gentoo-wiki.com/FAQ_Linux_Memory_Management)

Also, Firefox isn't a native KDE application, so it probably needs to load more libraries.

Since I use Firefox and Thunderbird on a regular basis on my laptop with only 256 MB of RAM, I can assure you it doesn't *require* 500 MB of RAM.

---

### Post by bimmerd00d on 2007-10-29
> **aysiu said:**
> Unused RAM is wasted RAM. Read more here:
[http://gentoo-wiki.com/FAQ_Linux_Memory_Management](http://gentoo-wiki.com/FAQ_Linux_Memory_Management)

Also, Firefox isn't a native KDE application, so it probably needs to load more libraries.

Since I use Firefox and Thunderbird on a regular basis on my laptop with only 256 MB of RAM, I can assure you it doesn't *require* 500 MB of RAM.

Also, using 64-bit on said machine.  My 32-bit Kubuntu on my laptop, and my g/f's laptop doesn't do this at all.  Currently posting from laptop and it's using a whopping 500mb out of 2GB with Firefox, Amarok, and Pidgin open.  I hate liking KDE and Gnome apps, there need to be 2 versions of each to make me all warm and fuzzy inside.

---

### Post by borris.morris on 2007-10-29
Why not use all the RAM available? Then you just programs that could be even faster....

---

### Post by bimmerd00d on 2007-10-30
> **borris.morris said:**
> Why not use all the RAM available? Then you just programs that could be even faster....

Because it begins to use the swap file when it fills up.  I have no problem using nearly all the RAM I have, but does it really need to be doing that?  Why does my 32bit install only require ~600-800mb of RAM, while my 64-bit needs 4GB?  That doesn't sound right to me.  Maybe 1200-1600 tops.

---

### Post by borris.morris on 2007-10-30
ok, that is a little troublesome. it deffinitly shouldnt need 4 gigs and start going to swap! you can go to KSysGaurd and look there for how much of what is being used. If it's disk swap, then it's probably a setting somewhere....

---

