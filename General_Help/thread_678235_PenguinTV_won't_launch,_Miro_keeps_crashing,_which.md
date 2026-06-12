---
title: "PenguinTV won't launch, Miro keeps crashing, which means  no media RSS reader"
date: 2008-01-25
forum: General Help
---

### Post by bg1256 on 2008-01-25
Seems the title has said it all.

I've installed both of these programs in synaptic, and both have worked before upgrading to Gutsy.

PenguinTV won't even launch. Whether I click the starter on my panel, in the menu, or via command line.

Here's the output:

```
gecko proxy settings up to date
initializing mozilla in /usr/lib/firefox
/usr/lib/python2.5/site-packages/penguintv/MainWindow.py:286: GtkWarning: Theme directory 32x32/stock of theme Oxygen-Gnome has no size field

  self.app_window.show_all()
/usr/lib/python2.5/site-packages/penguintv/MainWindow.py:286: GtkWarning: Theme directory 48x48/stock of theme Oxygen-Gnome has no size field

  self.app_window.show_all()
/usr/lib/python2.5/site-packages/penguintv/MainWindow.py:286: GtkWarning: Theme directory 64x64/stock of theme Oxygen-Gnome has no size field

  self.app_window.show_all()
/usr/lib/python2.5/site-packages/penguintv/MainWindow.py:286: GtkWarning: Theme directory 128x128/stock of theme Oxygen-Gnome has no size field

  self.app_window.show_all()
/usr/lib/python2.5/site-packages/penguintv/MainWindow.py:301: GtkWarning: gtk_window_resize: assertion `width > 0' failed
  self.app_window.resize(w,h)
Segmentation fault (core dumped)

```

Could it be as simple as changing icon themes?


Also, the only workaround I've found for miro is to mess around a lot with Java, something I really don't feel like doing. I don't want to cause problems with other programs I use that requier java.

any help would be appreciated.

---

### Post by bg1256 on 2008-01-27
Bump... any ideas?

---

### Post by Mos_Barbuta on 2008-01-28
I have the same problem with PenguinTV (Miro crashes sometimes but it's generally ok). I found this 
 [https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/131958](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/131958) 

and it seems the solutions posted there worked for some users. Personally I'm kind of new to Ubuntu (and loving every second of it) and strange and wondrous words like "schema files", 'CVS' and gconf and the fact that the only terminal command I know is ...wait...I don't know any commands (ok, I know a couple...)..you get the idea...i'm pretty much lost


Anyway, maybe it can help you
I still have a lot to go...

---

### Post by djrobthaman on 2008-01-28
I have the same problem with miro crashing constantly and almost immediately when I turned it on.  What I found, though, was that if when I turn it on I quickly change my view to the library or one of the channels as opposed to the channel guide it worked fine.  There must be something wrong with either the rendering engine or the channel guide itself.

Hopefully that helps.

---

### Post by bg1256 on 2008-01-30
> **Mos_Barbuta said:**
> I have the same problem with PenguinTV (Miro crashes sometimes but it's generally ok). I found this 
 [https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/131958](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/131958) 

and it seems the solutions posted there worked for some users. Personally I'm kind of new to Ubuntu (and loving every second of it) and strange and wondrous words like "schema files", 'CVS' and gconf and the fact that the only terminal command I know is ...wait...I don't know any commands (ok, I know a couple...)..you get the idea...i'm pretty much lost


Anyway, maybe it can help you
I still have a lot to go...

This is not much more than gibberish to me... I don't really know enough of the  linux lingo to understand what they're talking about.

Does anyone konw of an alternative to penguintv or miro?

---

### Post by bg1256 on 2008-01-30
Found a program in the repo called gpodder.

So far, it is working, although it doesn't have the features Miro does. For anyone else with this problem, have a look at gpodder if the solutions don't seem easy enough to follow.

---

### Post by james_xxx on 2008-02-10
I am having the same problem with Miro on my desktop, but oddly not on my laptop. I have no idea what the difference could be.

Miro is great, when it works, which is not often. I realize it has just reached 1.0, but I hope it will be less buggy and prone to crash in future. Otherwise, I am going to quit wasting time with it.


Anyone with suggestions on hom to get it working, please let us know!

---

### Post by FrozenFox on 2008-02-10
I'm not sure if this will help you, but I got Miro working w/o issue for me for the most part by following the advice here:

[http://linuxmint.com/forum/viewtopic.php?f=42&t=7045](http://linuxmint.com/forum/viewtopic.php?f=42&t=7045)

If that doesn't help you, I haven't followed the advice here since my stuff works, but perhaps this would help.

[http://linuxmint.com/forum/viewtopic.php?f=47&t=8170&st=0&sk=t&sd=a&hilit=miro](http://linuxmint.com/forum/viewtopic.php?f=47&t=8170&st=0&sk=t&sd=a&hilit=miro)

---

### Post by bg1256 on 2008-02-10
> **james_xxx said:**
> I am having the same problem with Miro on my desktop, but oddly not on my laptop. I have no idea what the difference could be.

Miro is great, when it works, which is not often. I realize it has just reached 1.0, but I hope it will be less buggy and prone to crash in future. Otherwise, I am going to quit wasting time with it.


Anyone with suggestions on hom to get it working, please let us know!


For the record, I have not gotten this to work.

For those skeptical of Miro in general, it does work quite well in Windows Vista.

It also works on my brother's Ubuntu Gutsy box without any spcial attention. It seems it's a blip on Ubuntu's radar and not Miro's.

for now, I'll stick with gpodder, and I'm hopping Hardy is a bit better than Gutsy.

---

