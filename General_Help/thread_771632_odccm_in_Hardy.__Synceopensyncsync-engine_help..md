---
title: "odccm in Hardy.  Synce/opensync/sync-engine help."
date: 2008-04-27
forum: General Help
---

### Post by VeeDubb on 2008-04-27
I know there are already a number of posts regarding the syncing of  Windows Mobile devices, and all of the related problems, but I have a new one.

With Gutsy, I was able to set up a 'mostly' usable sync setup with the directions at [http://www.synce.org/moin/SynceWithUbuntu](http://www.synce.org/moin/SynceWithUbuntu) 

It didn't work well, and I had to install some other synce-serial packages to work around a few of the bugs, but it was more or less functional.

I have tried to follow the directions there, after upgrading to hardy, and it seems that the odccm package, which is absolutely required if you're going to sync a WM5 or WM6 device, will no longer install.

Can anyone with a WM device give those directions a try and let me know if/how you were able to get odccm installed?  I've considered just compiling from source, but there are so many different versions of all these packages, with different patches and variations that it's like swimming up-stream to get this actually working.

Also, before anyone mentions what I have mentioned several times, I know that this is working with a single meta-package install if I use mandriva, but I've tried the mandriva 2008 spring release, and frankly, it sucks.  It's buggy, installing anything beyond the most basic applications breaks KDE, updates break KDE, installing a second WM breaks KDE, the Mandriva packages for KDE4 , while very stable, are badly incomplete and have none of the integration with the system that you would normally expect, and the Mandriva implementation of gnome is very unpolished, or at least it was last time I tried it.  So, I REALLY don't want to use Mandriva.

---

### Post by AdamWill on 2008-04-28
Well, as I said, it'd be great to discuss your issues with MDV in the MDV forums, as they're pretty unusual - not many people have that many problems, so there's obviously something odd going on with your install.

That aside, though, I'd recommend you go to #synce on Freenode IRC and ask in there. Particularly ask 'jc2k', who knows quite a bit about using synce / opensync on Ubuntu. I believe there are better packages in a third party repository somewhere.

---

### Post by VeeDubb on 2008-04-28
I will do that, but I have absolutely no hope in finding a solution there.  I have spent many hours trolling those mailing lists, with no success what so ever.

I was just hoping to find some other users here with similar experiences, because while Mandriva actually recognizes the popularity of these devices and the importance of their support, while Ubuntu does not, Ubuntu seems to have a MUCH larger contingent of people who use these devices and want to make them work.  Irony. 

As for discussing my problems at the mandriva forums, I'm not particularly interested.  the forums over at mandrivausers.org are a WONDERFUL resource, and the source of much of my Linux knowledge.  However, the undeniable fact remains that even before KDE breaks beyond usefulness (all window frames disappear, the keyboard won't respond, etc.) a clean install of Manriva 2008 spring pails in comparison to Ubuntu.  It's just not as well done.

---

### Post by nutpants on 2008-04-29
i have ocddm working in hardy

but for it to work i have to start it with odccm -f

then kill the process and do it again

then it works fine for me.( i get errors but they dont seem to affect anything)
( i installed it with the package manager.)

anything more than that i am still working on.
(like the opensync package trying to sync with evo2)

gdiepen here has been very help full
[http://ubuntuforums.org/showthread.php?p=4835375&highlight=opensync#post4835375](http://ubuntuforums.org/showthread.php?p=4835375&highlight=opensync#post4835375)

good luck
nutz

---

