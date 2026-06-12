---
title: "Amarok artist icons"
date: 2007-07-26
forum: General Help
---

### Post by tpg on 2007-07-26
On Ubuntu 7.04 (Gnome), I've just installed Amarok, but have noticed that the icon used for the artist is wrong in the collection tree view. [This thread]("http://ubuntuforums.org/showthread.php?t=281597&highlight=amarok+artist+icons") describes a problem pretty much identical to mine. I am guessing that the icons aren't installed as KDE isn't installed. I don't want to install the whole of KDE, so which package do I need to install to get the icons? Thanks in advance.

---

### Post by laidback on 2007-07-26
I find I have to left click and drag the disc icon to get the album icons to appear in tree view.
Also, cannot get any connection between the covers in Cover Manager and the music, this wasn't the case in an earlier version (currently using 1.4.6 in Feisty) where I could drag the cover onto my play list and the whole album appeared. Not so now unfortunately.

---

### Post by tpg on 2007-07-26
> **laidback said:**
> I find I have to left click and drag the disc icon to get the album icons to appear in tree view.
Also, cannot get any connection between the covers in Cover Manager and the music, this wasn't the case in an earlier version (currently using 1.4.6 in Feisty) where I could drag the cover onto my play list and the whole album appeared. Not so now unfortunately.
I think you have misunderstood: I am talking about the icons for the *artist*, not the album art. See the thread I linked to in the original post for a picture of what I mean.

---

### Post by laidback on 2007-07-26
Guess I have. Never seen icons for the Artists, if I have multiple albums under 1 artist when I click and drag all the albums for that artist appear overlaid, choose a single album lower down the tree and then just that one appears. To have an icon for the artist would be great.
I use Gnome.

---

### Post by tpg on 2007-07-27
Anybody else have any ideas? I've found a package called kde-icons-crystal, which probably has the required icons, but installing it requires installing pretty much the whole of KDE. Perhaps this ought to be filed as a bug against Amarok. What do people think?

---

### Post by bluknight on 2007-07-28
> **tpg said:**
> Anybody else have any ideas? I've found a package called kde-icons-crystal, which probably has the required icons, but installing it requires installing pretty much the whole of KDE. Perhaps this ought to be filed as a bug against Amarok. What do people think?

Not sure this is the same problem as yours but it may have some connections - there was a bug filed about icons disappearing and reappearing if certain theme icons are installed but to Ubuntu and not amarok:
[http://ubuntuforums.org/showthread.php?t=497296](http://ubuntuforums.org/showthread.php?t=497296)

Now my Amarok configure icons have gone away (not just the artist) as well as the side (column) icons. Im v happy to read your links that people have solved some icon problems using kcontrol from shell. I tried it and this is what I got:" Failed to open device
kdecore (KIconLoader): ERROR: Error: standard icon theme "crystalsvg"  not found!"

Ignore it and select KDEClassic icon theme. LOL my amarok icons returned :):)
Again it may not be your case, but I solved my problems.
SOLVED: cp -r crystalsvg to /usr/share/icons/ as default.kde link was mangled when kde was installed/de-installed

---

### Post by tpg on 2007-07-28
Well, I've tried installing the kde-icons-crystal package (it didn't actually want to install KDE as I said earlier - my mistake). However, the problem persists. I can't use the kcontrol command suggested in the other thread, because kcontrol isn't installed.

---

### Post by fmarier on 2007-12-11
You need to install the kdeartwork package.

Cheers,

Francois

---

