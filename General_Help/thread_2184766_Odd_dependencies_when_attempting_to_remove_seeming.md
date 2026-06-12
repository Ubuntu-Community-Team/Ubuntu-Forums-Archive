---
title: "Odd dependencies when attempting to remove seemingly unrelated packages"
date: 2013-10-30
forum: General Help
---

### Post by defaria on 2013-10-30
I have a bunch of software I don't want installed on my system. So I try to remove them but when I do I am warned that other packages will be removed. I fail to understand some of these dependencies. For example, I wish to remove tomboy or this hamster thing. When I go to do that it wants to remove gnome! I'm using gnome and things like gnome-panel. Why does apt-get want to remove gnome when I want to remove tomboy?

---

### Post by vasa1 on 2013-10-30
> **defaria said:**
> I have a bunch of software I don't want installed on my system. So I try to remove them but when I do I am warned that other packages will be removed. I fail to understand some of these dependencies. For example, I wish to remove tomboy or this hamster thing. When I go to do that it wants to remove gnome! I'm using gnome and things like gnome-panel. Why does apt-get want to remove gnome when I want to remove tomboy?
I can't answer your specific question but is this "gnome" a metapackage? If it is, that's quite a common response. See [https://help.ubuntu.com/community/MetaPackages](https://help.ubuntu.com/community/MetaPackages) and [http://www.mail-archive.com/lubuntu-desktop@lists.launchpad.net/msg03490.html](http://www.mail-archive.com/lubuntu-desktop@lists.launchpad.net/msg03490.html) (even though it's for Lubuntu) for more.

---

### Post by ian-weisser on 2013-10-30
```
$ apt-cache rdepends tomboy
tomboy
Reverse Depends:
  tomboy-latex
  tomboy-blogposter
 |screenlets-pack-basic
  screenlets-pack-all
  gnome-applets
 |gnome
  edubuntu-desktop
  unity-scope-tomboy

```

The *gnome* package (which is indeed merely a metapackage) requires Tomboy to be installed. So do all those listed packages.

You can safely remove Tomboy (and the Gnome metapackage).
Be aware that without the Gnome metapackage, important changes to Gnome (different applications, changed libraries) won't propagate to your system. Updates, of course, *will* continue to be applied.

---

### Post by defaria on 2013-11-01
OK, so I want to use the old gnome which is apparently called gnome-session-flashback with compiz. But in doing that it depends on gnome-screensaver. But I want to use xscreensaver. I can't remove gnome-screensaver without it removing gnome-session-flashback. What the F does gnome-session-flashback need gnome-screensaver? Face it, package dependencies in Ubuntu are hosed! They make things depend on other things for god knows what reason.

---

### Post by ian-weisser on 2013-11-01
The upstream (Gnome) developers set the dependencies, not the Debian and Ubuntu packagers.
You will need to ask your question to those Gnome developers.

You can always try compiling it yourself without the screensaver dependency.

---

