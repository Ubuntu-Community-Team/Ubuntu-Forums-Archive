---
title: "!!! Latest Compiz Update Break XGL/Compiz !!!"
date: 2006-09-04
forum: General Help
---

### Post by dr_d on 2006-09-04
FFS!!! I recently reinstalled my linux partition after attempts to fix the XORG bug messed everything up..

And just when I thinking that would be the last reinstall I'd be doing (until I upgraded to a 64 bit processor), the latest compiz updates have completely fcuked up my 3-d environment..

I'm using the [http://media.blutkind.org/](http://media.blutkind.org/) mirror (it's the only one which has gset-compiz).

Anyway, I'll wait a couple of days until a new update comes out and see if that fixes it, otherwise I think I'll move my desktop back to windows. I seriously cannot take the stress of reinstalling so many times.

Oh yeah, to anyone else who is running compiz, dont update it!

---

### Post by fxleytens on 2006-09-04
To late, I did (under a 32 bit environment) and it is all ****** up now !!!

Those updates where proposed by the "update-notifier" and the "update-manager" !!!

Does anyone has an idea ?

---

### Post by Lunar_Lamp on 2006-09-04
Well, I just updated using the quin repositories and have no problems.  However, I haven't tried logging out and back in, nor have I tried rebooting; I'm at work and really don't want to waste the morning getting my machine working again.  If you want to try using my repositories:

```
##added for xgl/compiz as per http://tazforum.thetazzone.com/viewtopic.php?t=21$
deb http://www.beerorkid.com/compiz/ dapper main
deb http://xgl.compiz.info/ dapper main
deb-src http://xgl.compiz.info/ dapper main
```

If you want to try and downgrade the packages you just upgraded try this syntax (note the equals sign to denote the version number):

sudo apt-get install PACKAGE-NAME=FULL-PACKAGE-VERSION-NUMBER

Of course, you'll need to know which packages to downgrade.

I should also point out that xgl/compiz is really in a very unstable place at the moment; it's alpha software at best.  It's really to be expected to crash a lot, and I'm sorry if you didn't realise that when you installed it, but wherever you got instructions from should really have told you to expect it to make your computer break down and cry.


> Those updates where proposed by the "update-notifier" and the "update-manager" !!!
The update manager and update-notifier use your entire sources list.  They are not restricted to official sources unless your sources list is restricted to official sources.

---

### Post by Farbi on 2006-09-04
I'm using the same repo's as you.  I can log into my XGL/Compiz session and the only difference between in and the standard Gnome session is that metacity isn't running... So I consider it to be broken (oh yeah and if I try to do anything that is even remotly considered 3d (glxgears...) hard crash).  My first thought was that something got messed up in the settings and so I got a terminal open (right-click create launcher... (altf2 didn't work, and panels were mysteriously missing) and brought up gconf-editor.  Then I thought to myself hmmm that's odd everything in it has settings that I can change.. accept compiz.  everything is blank accept compiz>General>allscreens>options.  and the only thing listed there is audible bell.  Everyother expandable tree is blank.  Is this because it didn't load? (<--- slight noob, fresh XP uninstaller).  Just thought I'd add that cause I didn't see anything else said about it.  Would love to see a fix for it, cause I love my wobbly windows, transparency, and my 6sided "cube".


otherwise I this forum is the most helpful I've ever seen
Thanks to all who help 
:~)
Farbi

---

### Post by heng on 2006-09-04
It really does help to read the update logs when playing with experimental software. At least after the fact if it doesn't work.

Gconf is no longer used. Try loading compiz with the compiz-start script instead of some homebrew affair. That solved the problem on my machine.

As regards dr_d's comments about being unable to cope with problems - I suggest you stick to stable software.

---

### Post by kwaanens on 2006-09-04
Try this: [http://www.compiz.net/topic-3862-quinn-compiz-with-latest-compiz-plugins-update](http://www.compiz.net/topic-3862-quinn-compiz-with-latest-compiz-plugins-update)

---

### Post by usergentoo on 2006-09-04
open a terminal and type compiz-start 
that fixed my problem made me a little nervous for a minute

---

### Post by calvinthomas on 2006-09-04
As said above but put it in startup, go to system > preferences > sessions, go to the startup tab and add compiz-start (also take out any other you might have if you want I had /usr/bin/compizstart) then reboot and it'll all be working perfectly

Calv

---

### Post by Dinerty on 2006-09-04
Ok guys heres how I fixed my xgl/compiz after todays new updates, did abit of searching around on these forums and on compiz.net and found that the new updates use "csm" instead of gconf now:

```
compiz-start
```

then

```
chmod 755 ~/.compiz -R
```

then

```
csm
```

Configure everything to way it was before, then finally add this line to your "Sessions > Start up programs"

```
/usr/bin/compiz-start
```


**Big thanks to all the guys on here and compiz for this quick fix !

---

### Post by dr_d on 2006-09-04
nice. many thanks heng.

i'm so glad i waited before nuking my nix partition.. i've been so happy to see my favourite wobbly back in action :)

aiiite i got to go get my wobble on..

thanks again!

---

### Post by toasted on 2006-09-04
And you will no longer need the red icon if you have it ... disable that in sessions/startup programs (or delete it)

---

### Post by skroll on 2006-09-04
> **dr_d said:**
> FFS!!! I recently reinstalled my linux partition after attempts to fix the XORG bug messed everything up..

And just when I thinking that would be the last reinstall I'd be doing (until I upgraded to a 64 bit processor), the latest compiz updates have completely fcuked up my 3-d environment..

I'm using the [http://media.blutkind.org/](http://media.blutkind.org/) mirror (it's the only one which has gset-compiz).

Anyway, I'll wait a couple of days until a new update comes out and see if that fixes it, otherwise I think I'll move my desktop back to windows. I seriously cannot take the stress of reinstalling so many times.

Oh yeah, to anyone else who is running compiz, dont update it!

You know, Gset-compiz has gone the way of the dodo quite awhile ago, and you should stop suing it.  Especially since compiz no longer uses gconf at all to read its settings.  Use csm now instead.

---

### Post by dr_d on 2006-09-07
Oh ok i had no idea... Hmmmm I'll check out csm

---

