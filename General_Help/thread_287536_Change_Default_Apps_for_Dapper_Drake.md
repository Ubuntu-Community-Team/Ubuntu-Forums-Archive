---
title: "Change Default Apps for Dapper Drake"
date: 2006-10-28
forum: General Help
---

### Post by undertakingyou on 2006-10-28
I'm using Dapper Drake GNOME  and I have set up a keyboard shortcut for things like "open music APP" etc.  Whenever I hit this it opens rhythmbox.  I don't want it to open rhythmbox, I want it to open Amarok.  Is there somewhere that I can change that?  I also want my forward and back keys to work in amarok.  I'm hoping that will work once I change the default music APP.  Thanks,
Will Smith--

---

### Post by hearnden on 2006-10-28
There are some programs (web browser, mail reader and terminal) that are controlled by System->Preferences->Preferred Applications, but music players aren't there.  Programs triggered by removable drives (e.g. mp3 players) are controlled by System->Preferences->Removable Drives and Media, but there is no 'open music' setting.  Aren't the details of which program gets launched in the shortcut itself?  Or is this a special GNOME shortcut?

---

### Post by undertakingyou on 2006-10-28
This seems to be a GNOME "special shortcut."  It is made by going to SYSTEM => PREFERENCES => KEYBOARD SHORTCUTS.  After that you just go down and set your shortcut for "Music Player"  It doesn't give an option for which one and I tried to find it in gconf-editor.  Can't seem to find it there.  Any thoughts?
Will Smith--

---

### Post by hearnden on 2006-10-30
Have a look here:  [https://launchpad.net/products/control-center/+bug/4265](https://launchpad.net/products/control-center/+bug/4265)

Apparently "rhythmbox" is hardcoded as GNOME's music player.  Looks like we're stuck with it until an upgrade, unless you want to tinker with the sources.

---

### Post by undertakingyou on 2006-10-30
Thanks for looking it up.  I hope they actually fix that.  You would think they would with Dapper and now Edgy.  Well, I haven't tried it with Edgy but I will.  Thank again.
Will Smith--

---

### Post by xnn on 2006-11-05
It's fixed in Edgy now (tested on Kubuntu).

---

### Post by undertakingyou on 2006-11-06
Ok, if it is fixed in Edgy, where do I go to change it?  I did an edgy update, looked all through gconf-editor with no results.  
Thanks,
Will Smith--

---

### Post by hikaricore on 2006-11-06
I discovered a very lazy fix for this awhile back.

From terminal type:

```
whereis rhythmbox
```

then:

```
sudo mv /locationofrhythmbox/rhythmbox /locationofrhythmbox/rhythmbox2
```
^where /locationofrhythmbox/ is the dir the prog is located probably something like /usr/bin/rhythmbox but I removed it on my system so I can't tell ya for sure.

then:

```
cd /usr/bin
```

```
whereis amarok
```

```
sudo ln -s /locationofamarok/amarok rhythmbox
```
^where /locationofamarok/amarok is the location (you get the point by now)

Basicly you're softlinking your amarok app to the name rhythmbox, so when you hit the media key it will open instead :)

Cheap hack?  Yes.  Does it work?  More than likely.

hope this helps.

---

### Post by undertakingyou on 2006-11-06
Thanks, I set up a symlink with the name rythmbox that points to Amarok.  I think amarok is the best player in the world.  So it is working, I am wondering if I updated to edgy for nothing though.

---

### Post by hikaricore on 2006-11-06
There is probably a way to change is in edgy, I just havn't looked for it.  If nothing else maybe your system will run more smoothly in edgy?  I know mine does :)

---

### Post by strabes on 2006-11-13
I have a blog post about pretty easily creating custom keyboard shortcuts here: 
[http://strabes.wordpress.com/2006/11/13/create-custom-keyboard-shortcuts-in-ubuntu/](http://strabes.wordpress.com/2006/11/13/create-custom-keyboard-shortcuts-in-ubuntu/)

You'll probably have to disable your old keyboard shortcut so they don't conflict.

---

### Post by [d3v] on 2006-11-13
> **xnn said:**
> It's fixed in Edgy now (tested on Kubuntu).

The issue is that it is hard coded as the default in Gnome. KDE most likely doesn't have the same bug.

From what I have seen (and I am running Edgy now) the symlink is the only way of doing it without modifying Gnome. Surely it wouldn't be too hard to link it using /etc/alternatives... :-k maybe I when get some spare time I can look into it... but that could be a while ;)

---

### Post by TheValk on 2007-01-02
Here's how I did it in Edgy
Right click on a file of the type in question
Choose Properties (at the bottom of the menu)
Choose the 'Open With' Tab
Double click on the chosen application in the list given so that the  app circle is 'dotted'
Jobs a good'un.
I hope I understood the question?

---

### Post by [d3v] on 2007-01-03
> **TheValk said:**
> Here's how I did it in Edgy
Right click on a file of the type in question
Choose Properties (at the bottom of the menu)
Choose the 'Open With' Tab
Double click on the chosen application in the list given so that the  app circle is 'dotted'
Jobs a good'un.
I hope I understood the question?

The problem isn't setting a program to open a file when you try to open a music file, it is binding the "Open Music Player' (or equivilant) to a different music player than Amarok. It is indeed possible to set the default player to Amarok for mp3's but if you press the Music Player multimedia key on the keyboard, you get Rhythm Box unless you do the symlink hack.

Don't get me wrong, the symlink works but I would prefere to be able to use alternatives. As of yet, still no time to work on making work like that :-|

---

### Post by TheValk on 2007-01-04
Yep, I didn't understand the question  ](*,)

---

### Post by Jeremiah478 on 2007-01-13
Thanks hikaricore, I used your "cheap hack" and it work perfect; best kind!

---

