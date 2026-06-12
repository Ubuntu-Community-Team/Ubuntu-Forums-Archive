---
title: "Do you agree that KDE should be more modular?"
date: 2007-11-30
forum: General Help
---

### Post by TDK800 on 2007-11-30
Imho, it sucks that you are unable to separately un-install e.g. Games or KSnapshot or OpenOffice Drawing from KDE without it saying that one or more applications depend on that app.. so I have like 40 apps in KDE that I will probably never use and are just clutter there... am I the only one here who think KDE should be re-designed to be more modular? 

For example when you look at MTA's PostFix kicked Sendmail's *** due to it's modular design.

---

### Post by p_quarles on 2007-11-30
KDE is in fact very modular. I think what you're running into here is the "kubuntu-desktop" metapackage. It is completely safe to remove that (since it's not really a package -- it's a list of dependencies that give you the full-featured Kubuntu setup). If you try to remove one of its dependencies, it will indicate that it's going to remove the metapackage as well -- and that's all it should do. 

Here's a link to the page that describes the kubuntu-desktop package:
[http://packages.ubuntu.com/gutsy/metapackages/kubuntu-desktop](http://packages.ubuntu.com/gutsy/metapackages/kubuntu-desktop)

---

