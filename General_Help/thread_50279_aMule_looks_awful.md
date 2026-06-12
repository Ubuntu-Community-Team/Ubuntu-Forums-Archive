---
title: "aMule looks awful"
date: 2005-07-19
forum: General Help
---

### Post by scorpio2002 on 2005-07-19
Hi there! I've just installed amule and I must admit that it really looks awful in ubuntu. I've seen it in other Gnome based distros, but believe me when I say that the text is really too HUGE and looks like your monitor is 600x800 instead of 1024x768...

is there anything I can do to make it a little bit more "human"? :D

---

### Post by ounn on 2005-07-19
Try the cvs version. Just be sure that you have wxwidgets instaled.

ounn

---

### Post by cutOff on 2005-07-19
[QUOTE=scorpio2002]Hi there! I've just installed amule and I must admit that it really looks awful in ubuntu. I've seen it in other Gnome based distros, but believe me when I say that the text is really too HUGE and looks like your monitor is 600x800 instead of 1024x768...

is there anything I can do to make it a little bit more "human"? :D[/QUOTE]
Try

```
$ sudo aptitude install xfonts-100dpi-transcoded xfonts-75dpi-transcoded xfonts-base-transcoded
```

---

### Post by scorpio2002 on 2005-07-19
> Try the cvs version. Just be sure that you have wxwidgets instaled

Where can I get the cvs? I checked in Synaptic, and I cam't see wxwidgets :|

> $ sudo aptitude install xfonts-100dpi-transcoded xfonts-75dpi-transcoded xfonts-base-transcoded

That didn't work.

---

### Post by ounn on 2005-07-19
Sorry tha name of the package is libwxgtk2.5-dev.

You can get a aMule copy from the cvs here [http://www.hirnriss.net/?area=cvs](http://www.hirnriss.net/?area=cvs) 

the you have to compile aMule.
just make this

./configure
make
make install

I dont remember if i need more packages to compile this, but if you get errors in configure just pay atention to packages that are missing and instal the corresponding dev package with synaptic.

Be sure that you first uninstall aMule that you get from synaptic.

ounn

---

### Post by ow50 on 2005-07-19
Try my GTK2 deb package for Hoary:
[amule_2.0.3-1build1~ots_i386.deb](http://koti.mbnet.fi/ots/linux/hoary/amule_2.0.3-1build1~ots_i386.deb)

Read this topic for details:
[http://www.ubuntuforums.org/showthread.php?t=31395](http://www.ubuntuforums.org/showthread.php?t=31395)

---

### Post by Burgundavia on 2005-07-19
Amule looks awful due to a bug in WxWidgets. Basically the wxwidgets in hoary is linked against GTK 1.x.

Wxwidgets 2.6 (which is about to hit breezy), solves this by linking it against GTK 2.x

Corey

---

### Post by cutOff on 2005-07-19
[QUOTE=scorpio2002]That didn't work.[/QUOTE]
Sorry for that. Let me say you can uninstall them by

```
sudo aptitude remove xfonts-100dpi-transcoded xfonts-75dpi-transcoded xfonts-base-transcoded
```
Sorry again

---

### Post by lol on 2005-07-20
Using gtk1 is not really a problem. Ok, it's less beautiful than gtk2 but it's far from being "awful".

And there is a good reason to stick to wx2.4/gtk1 right now: stability and memory leaks. On Debian (unstable), aMule and hugin were at some point linked against gtk2 (using wx2.6), but after less than 2 weeks they reverted back to gtk1... too many problems.

Now, if aMule (and xmms and all other gkt1 apps) really is awful (ugly fonts), then there is another problem. The best way to try to solve this is simply to delete all ".gtkrc" file in your home. At least it worked for me.

---

### Post by scorpio2002 on 2005-07-20
Thank you a lot! I installed libwxgtk2.5.3 and then the -deb package you gave me(amule 2.0.3). Now it looks really fine :-)

---

