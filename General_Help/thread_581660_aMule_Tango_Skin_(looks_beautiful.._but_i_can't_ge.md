---
title: "aMule Tango Skin (looks beautiful.. but i can't get it to work)"
date: 2007-10-19
forum: General Help
---

### Post by cvaty on 2007-10-19
look at this great amule tango skin...
[http://generalmidi.deviantart.com/art/aMule-Tango-Gnome-54081576](http://generalmidi.deviantart.com/art/aMule-Tango-Gnome-54081576)

He even claims it works with the latest version 2.1.3 and ubuntu...
i can't get it to work for the life of me... can any here do it and explain how?

**SOLVED**:
you need to latest cvs of amule to get this to work...
the latest cvs of amule has 4 skins included by default: tagno, gnome, kde, and xfce
if you want to download the latest cvs and try it,
heres the link: [http://www.hirnriss.net/?area=cvs](http://www.hirnriss.net/?area=cvs)

(10/21 didn't work for me but 10/20 did) 
(if your reading this in the future, dont worry about these dates and just get the latest one)
(if your reading this so far in the future that amule 1.2.0 has allready been released, just download that, and go to prefrences, gui.  it should be included and working when it is released.

good luck to all

---

### Post by cvaty on 2007-10-21
come on people, i know at least a few of you must use amule. and i know of the few that do, all of you think its ugly as sin.  bump?

---

### Post by cvaty on 2007-10-21
... i'm not about to give up on this one...

these forums are great, but if you have a question that no one knows the answer to, no one trys to figure it out

---

### Post by cvaty on 2007-10-22
la la la

---

### Post by ruibernardo on 2007-10-22
> **cvaty said:**
> 
He even claims it works with the latest version 2.1.3 and ubuntu...
i can't get it to work for the life of me... can any here do it and explain how?

Well, if you tried it, what errors you got? Run amule from a terminal and post the errors here. Maybe you just need to install a package or something.

---

### Post by cvaty on 2007-10-22
cvaty@cvaty-laptop:~$ amule
Initialising aMule
Checking if there is an instance already running...
No other instances are running.
Testing skins
Loading temp files from /home/cvaty/.aMule/Temp.

All PartFiles Loaded.
ListenSocket: Ok.

External connections disabled in config file
*** Server UDP socket (TCP+3) at 0.0.0.0:4665
*** TCP socket (TCP) listening on 0.0.0.0:4662
*** Client UDP socket (extended eMule) at 0.0.0.0:4672


nothing useful there  (as far as i can see)

---

### Post by ruibernardo on 2007-10-22
So amule doesn't die. What's the problem then?

---

### Post by cvaty on 2007-10-22
the problem is, it isn't skinned.  and i'd like it to be.

---

### Post by cvaty on 2007-10-22
let me try with the latest cvs instead of the ubuntu package...
one moment

---

### Post by ruibernardo on 2007-10-22
I tried to install the skin, I didn't moved the file to /usr/share/amule, I've just decompressed it in a directory and then I opened amulegui, went to Preferences, Graphic interface settings, checked "use theme file..." and selected the file (portuguese here, but the options should be something like that). This should work in amule.

Did you tried that way?

I'm using amule-daemon with amulegui. It didn't work with amulegui. No theme/skin here, but amulegui is different from amule (desktop).

---

### Post by cvaty on 2007-10-22
mmm... i'm a moron, the cvs from yesterday works great, even comes with 4 default skins: tango, gnome, kde and xfce... i'm looking forward to the next release...

heres a screen shot of amule skinned on my pc just for the heck of it:


if you want to download the latest cvs and try it,
heres the link: [http://www.hirnriss.net/?area=cvs](http://www.hirnriss.net/?area=cvs)

NOTE: 10/21 wouldn't ./configure for me
10/20 worked great...

---

