---
title: "Usplash wont work."
date: 2007-06-17
forum: General Help
---

### Post by loathsome on 2007-06-17
Hi there,

Just removed Ubuntu and installed Kubuntu, and now I don't have usplash when booting (I see all that text etc.)
When I launch usplash from konsole or equivalent, the screen goes black for two seconds then returns to my desktop.

I've tried [COLOR="DarkSlateGray"]**$ dpkg-reconfigure usplash**[/COLOR] without any luck. I even tried to install the «edubuntu-artwork-usplash» package, but that didn't work either.

Any idea what I should try?

Thanks,
loathsome

---

### Post by loathsome on 2007-06-17
I think I solved this out. Just ran **[COLOR="DarkSlateGray"]$ sudo update-alternatives --config usplash-artwork.so[/COLOR]**, and now **[COLOR="DarkSlateGray"]$ usplash[/COLOR]** displays the kubuntu splash screen.

I'll see next boot! :)

---

### Post by loathsome on 2007-06-17
Yep, that did the trick!

---

