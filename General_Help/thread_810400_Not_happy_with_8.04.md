---
title: "Not happy with 8.04"
date: 2008-05-28
forum: General Help
---

### Post by G_Stewart on 2008-05-28
I love Ubuntu, but the new version is disappointing. First I cant hide the panel, Second, I keep losing my background image every time I shut down and third (so far) it keeps telling me there is a version of Thunderbird running already whenever I try to start it. There isn't, Ive even rebooted. LOL

I just don't want to go through the hassle of downgrading.

Oh yea, I am using KDE 4

Gary

---

### Post by Zorael on 2008-05-28
I don't recommend KDE 4 to anyone at this point; wait until 4.1.0 is released, I say. KDE 3.5.9 is pretty much rock stable, with only some minor lingering bugs.

If you wish to remove KDE4 and grab KDE3 instead, do this in a terminal.
```
$ sudo aptitude install kubuntu-desktop ~nkde4_
```
Should work. It'll install kubuntu-desktop and purge all packages containing 'kde4', which has done the trick for me several times.

---

### Post by roderick on 2008-05-28
I agree. KDE 3.5.9 = Rock Solid. KDE 4.0 = Use at your own Risk (not recommended for daily use).

That was pretty clear on the Download Page for the 8.0.4 release.. not sure if you missed it. :)

---

### Post by G_Stewart on 2008-05-29
Thanks guys, that did the trick.

Gary

---

