---
title: "where are the applications?"
date: 2008-02-13
forum: General Help
---

### Post by oui on 2008-02-13
bonjour

I use  in my partition hda6 a ext2-partition for Kubuntu 7.10 remastered with KDE4 from Ubuntu site on an DELL Optiplex SX270 with Celeron

In the very hard to use KDE4 menu I don't find different applications being in it, so Kwrite or Kate. I only know that they are in it because they open by clicking on text files!

/usr/local/bin is empty!

where are the applications (I miss a viewer for video as [http://jt.france2.fr/20h/](http://jt.france2.fr/20h/) or youtube videos). and where are the codecs / plugins? what ist easier to install: Xine with codecs for Konqueror, or Mplayer, or VLC? my experience it that this part of Linux is very critical :(

where is java? I see only static picture on the page [http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml) . the dancing Duke don't dance!

salut


salut

---

### Post by apetresc on 2008-02-13
> **oui said:**
> /usr/local/bin is empty! Try /usr/bin.

> **oui said:**
> where is java? I see only static picture on the page [http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml) . the dancing Duke don't dance!
Do a ```
sudo apt-get install sun-java6-jre sun-java6-plugin
```

---

### Post by Trail on 2008-02-13
You know, KDE 4.0.0 is not as stable and functional as a standard release. It's more intended for developers.

If you want a more usable environment, use KDE3.5 or Gnome.

---

### Post by oui on 2008-02-14
bonjour

> **Trail said:**
> You know, KDE 4.0.0 is not as stable and functional as a standard release. It's more intended for developers.

If you want a more usable environment, use KDE3.5 or Gnome.

thank you very much! where is the place (in which forum) where developers discuss about KDE 4 usage and experience in the environment of Kubuntu?

a part of my beginner problem is to find in little errors may be easy to eliminate like, only an exemple, the Dolphin icon don't appairs in the start menu (but appairs in the task bar). the consequence is that the function "add to panel" can't work at all if you try to do it, etc.

this morning, I have more experience with KDE4 and thing about to install it on my second computer.

salut

---

### Post by utUtu on 2008-02-14
> **oui said:**
> bonjour

I use  in my partition hda6 a ext2-partition for Kubuntu 7.10 remastered with KDE4 from Ubuntu site on an DELL Optiplex SX270 with Celeron

In the very hard to use KDE4 menu I don't find different applications being in it, so Kwrite or Kate. I only know that they are in it because they open by clicking on text files!

/usr/local/bin is empty!

where are the applications (I miss a viewer for video as [http://jt.france2.fr/20h/](http://jt.france2.fr/20h/) or youtube videos). and where are the codecs / plugins? what ist easier to install: Xine with codecs for Konqueror, or Mplayer, or VLC? my experience it that this part of Linux is very critical :(

where is java? I see only static picture on the page [http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml) . the dancing Duke don't dance!

salut


salut

They are in /usr/lib/kde4

---

