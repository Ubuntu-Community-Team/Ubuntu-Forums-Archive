---
title: "installed kreski lines gnome icon theme.  folder icons did not change however, help"
date: 2008-04-25
forum: General Help
---

### Post by kraymore on 2008-04-25
I installed kreski-lines icon theme for gnome and my folder icons instead of getting the new look from the theme, reverted to standard gnome folders.

I've seen the folder icons for this package and its not adopting it for some reason.  seems to be stuck on native gnome icons for folders.  :( help

---

### Post by Anduu on 2008-04-26
I have noticed a lot of the older icon themes don't function properly nowadays.

I think the way Gnome handles icon themes has changed in recent versions and older themes need to be updated.

---

### Post by sanderDrost on 2009-08-24
is there anyway to fix that, the theme looks real cool.

---

### Post by kraymore on 2009-08-24
I was never able to get kreski lines to work when installing from an archive.  I too would be interested if anyone know how to get it to work ib say jaunty or karmic.

thank you

---

### Post by sanderDrost on 2009-08-25
is there a way to copy the icons to another, working, theme maybe?

---

### Post by tristano on 2010-03-12
While not a solid fix, I was able to work around the missing folder icons by doing the following:
```

cd ~/.icons/Kreski-Lines/
mkdir scalable
cd ~/.icons/Kreski-Lines/64x64/filesystems/
cp gnome-fs-directory.png folder.png

```

Not sure why, but the "scalable" directory needs to exist as well as the folder.png file.

I also recommend editing ~/.icons/Kreski-Lines/index.theme and setting the "Inherits" setting to be another installed theme that you like that kinda fits the style. The top of my index.theme file now looks like this:
```

[Icon Theme]
Name=Kreski Lines
Comment=Kreski Lines by azazel100
#Inherits=Industrial
Inherits=Magog White

```

It's a bit of a hodgepodge overall with the two themes, but at least my desktop looks right...

---

### Post by ahoora on 2010-11-10
You can get my version of the modified icon set from:

[http://db.tt/4IKIxpf](http://db.tt/4IKIxpf)

This is in no way complete, it was for personal use and I thought I'd share it.

*edit: this was called 'Nerdy-Lines' when I downloaded it from gtk art website. It seems it's based on Kreski-Lines and it's the svg (scalable) version of Kreski

---

### Post by silentstone on 2010-12-30
I started picking at this theme, too.  Just copied some of the emblem icons to apps and categories, renamed.  I merged my changes with yours, ahoora.  Still not satisfied with it, but some icons actually show up now on my Ubuntu 10.04 desktop and menu.

And this is with Nerdy Lines.

---

