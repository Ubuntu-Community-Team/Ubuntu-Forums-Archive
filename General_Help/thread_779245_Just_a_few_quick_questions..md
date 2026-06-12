---
title: "Just a few quick questions."
date: 2008-05-02
forum: General Help
---

### Post by cloroxmartini on 2008-05-02
Alright, this is a really dumb question but I am new to Ubuntu and Linux and I need to learn how to install programs.  I downloaded Compiz but I don't know how to install.  I also need to know which program to download so I can watch YouTube videos.

---

### Post by Achtung on 2008-05-02
In the last 2 versions of Ubuntu, compiz-fusion is installed by default, so you don't have to download and install seperately. Click System/preferences/appearance/Visual effects and select something other than "none". You need the restricted drivers for your video card installed for this to work!

You'd also better install the compizconfig-settings-manager, which is not installed by default. Click System/administration/synaptic package manager and search for "compizconfig-settings-manager". Mark for installation, and apply. You can now tweak your compiz-fusion install through System/preferences/advanced desktop effects settings.

BTW, if you downloaded a "compiz" package (as opposed to a "compiz-fusion" package), it's obsolete. You can delete it. 

While you have synaptic open, search and install "ubuntu-restricted-extras". This package contains most codecs needed for multimedia playback, including the flash plugin needed to see youtube videos.

If you search for these and cannot find them through synaptic, you probably don't have all the repositories enabled. Click System/administration/software sources and tick "main", "universe", "restricted" and "multiverse".

---

### Post by cloroxmartini on 2008-05-03
Thanks, that's pretty cool.

---

### Post by cloroxmartini on 2008-05-03
Okay, here's a few more questions...

I'm using the Beryl Theme Manager but one thing I find annoying is that only the windows take the theme and the panels stay the same.  Now I've seen screens and videos on YouTube and I see that the panels can also change...How can I make the panels take the theme as well?

Also, I installed the multimedia stuff and YouTube videos do play, but all multimedia/flash stuff on the internet does not automatically play and instead has a giant gray "play" button that I have to press in order for them to start playing, even with the adds.  If I don't think about it, it doesn't bother me, but is there anyway to get all the flash and the like to automatically come up?

---

