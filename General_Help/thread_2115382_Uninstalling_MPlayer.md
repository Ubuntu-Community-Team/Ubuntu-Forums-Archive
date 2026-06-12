---
title: "Uninstalling MPlayer"
date: 2013-02-12
forum: General Help
---

### Post by ooleyguy on 2013-02-12
I use VLC to play video and Rythmbox for audio and don't need MPlayer and a few other apps, but when I try to remove them using the software manager, it tells me that gnome-core will be removed as well. Is this true? Will I remove gnome just because I want to remove some piece of unneeded software?

---

### Post by Yellow Pasque on 2013-02-12
gnome-core is a metapackage. Removing it will not remove gnome.

---

### Post by ooleyguy on 2013-02-12
Woohoo, so the other ones that say they are going to uninstall xfde, KDE Plasma, etc. are just meta packages too?

---

### Post by unheeding on 2013-02-12
> **ooleyguy said:**
> Woohoo, so the other ones that say they are going to uninstall xfde, KDE Plasma, etc. are just meta packages too?

Yes, for example xubuntu-desktop depends on all the packages included with xubuntu, if you remove one of them, it will also remove the xubuntu-desktop metapackage, but shouldn't remove XFCE.  Be careful though.

---

### Post by 3Miro on 2013-02-12
Install Synaptic Package Manager, it will give you more verbose information about what packages depend on what, what installs what and what will be removed if you remove something.

---

