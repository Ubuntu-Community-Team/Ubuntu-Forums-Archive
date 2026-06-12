---
title: "Big bad problem with libc6 2.6.1 on Feisty"
date: 2007-10-01
forum: General Help
---

### Post by Cyvros on 2007-10-01
I have a big, big problem. While trying to install libqt4-core 4.3.1, I saw that I had an unsatisfied dependency of libc6 2.6. So I went in search of a package for it. I found one via the Ubuntu packages site. I installed it and I do believe that I installed a package meant for Gutsy.

Synaptic tells me that the current libc6 installation from the repos is broken, which makes sense. But I'm told that I must remove all of this:

```
build-essential
comerr-dev
g++
g++-4.1
gnome-common
libart-2.0-dev
libasound2-dev
libatk1.0-dev
libaudiofile-dev
libavahi-glib-dev
libbonobo2-dev
libbonoboui2-dev
libc6-dev
libc6-i686
libcario2-dev
libdebus-glib-1-dev
libesd0-dev
libexpat1-dev
libfontconfig1-dev
libfreetype6-dev
libgconf-dev
libgconf2-dev
libgcrypt11-dev
libgl1-mesa-dev
libglade2-dev
libglib2.0-dev
libglu1-mesa-dev
libglu1-xorg-dev
libgnome-desktop-dev
libgnome-keyring-dev
libgnome-vfs-dev
libgnome2-dev
libgnomecanvas2-dev
libgnomeui-dev
libgnomevfs2-dev
libgnutls-dev
libgtk2.0-dev
libidl-dev
libjpeg62-dev
libkrb5-dev
liblzo-dev
libmetacity-dev
libmng-dev
libncurses5-dev
liboaf-dev
libopencdk8-dev
liborbit2-dev
libpango1.0-dev
libpng12-dev
libpopt-dev
libpq-dev
libqt4-dev
libsqlite0-dev
libssl-dev
libstdc++6-4.2-dev
libtool
libwnck-dev
libwxbase2.8-dbg
libwxbase2.8-dev
libwxgtk2.8-dbg
libwxgtk2.8-dev
libxft-dev
libxml2-dev
python-gtk2-dev
qt4-designer
ubuntu-minimal
xlibmesa-gl-dev
zlib1g-dev
```

I find that a very scary list, especially since ubuntu-minimal is listed there.

Via Synaptic, I tried reinstalling everything, but it still tells me that I can't do a thing without removing the broken packages.

So I tried another way, by uninstalling libc6 (not actually uninstalling it, but trying out things with package marking in Synaptic). But just about everything requires it, so I'd be removing a lot of apps, including at least a dozen essential packages, which I really, **really** don't want to do. I tried uninstalling everything that requires libc6, then reinstalling everything while still making libc6 isn't installed, to see what that would do, but it still needs libc6.

Is there some way to make it 'see' libc6-i686 as libc6 so I can lose the newer package? Or is there some way to keep the newer package and lose the old one without losing packages that look really really necessary?

Can anyone help me? Please? :)

---

### Post by por100pre1 on 2007-10-01
Try opening Synaptic, find libc6, it should be 2.5. Click it and then press Ctrl+E. You should then be given the opportunity to force the Feisty version.

Hope it helps. :)

---

### Post by disraeli on 2007-10-01
I had a similar problem and I DID remove some apps, including ubuntu-minimal, though I didn't do this on purpose. My problem was with libc6 too (which I needed for updating Sound Juicer); Synaptic was telling me it couldn't install nor remove packages because it needed some exact version installed first (something like libc6=2.5-0ubuntu7). So I opened up a terminal and installed that exact version through apt-get install. The installation went fine, I started Synaptic and made it repair the rest, and succesfully-reinstalled the lost packages including ubuntu-minimal.

---

### Post by Cyvros on 2007-10-01
Aha! Thank you, sirs (or madams, as the case may be)! My heartiest gratitude and my compulsive package installation disorder thanks you. :D

---

