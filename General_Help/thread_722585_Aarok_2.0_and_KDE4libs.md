---
title: "Aarok 2.0 and KDE4libs"
date: 2008-03-12
forum: General Help
---

### Post by Nimaran on 2008-03-12
I was messing around on KDE and Kubuntu and decided to add this repository:

```
deb http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu gutsy main
```

I then installed:

```
sudo apt-get update && sudo apt-get install amarok2 amarok2-phonon
```

I tried it out and decided I wanted to get red of it, I hadn't realized that it is not near ready to be a everyday usable audio player....yet (I have great hopes)

I would now like to get rid of all the libs and amarok 2.0 that it installed is their a way to do that besides manually tracking down every single thing it installed and removing it via adept one at a time.

Thanks in advance :)

---

### Post by g2g591 on 2008-03-12
simple, 
sudo apt-get purge amarok2 amarok2-phonon , then sudo apt-get autoremove

---

### Post by Nimaran on 2008-03-12
Okay, that worked some, but when I installed it installed a hundred some megs of kde4 libs, and the commands you told me only removed a few packages.

---

### Post by fifth on 2008-03-12
> **Nimaran said:**
> Okay, that worked some, but when I installed it installed a hundred some megs of kde4 libs, and the commands you told me only removed a few packages.

If your not using KDE4 or KDE4 apps, why not use synaptic to search for'kde4' and remove the installed components? (Obviously double checking the descriptions and version numbers before selecting to remove).

---

### Post by Nimaran on 2008-03-12
Is KDE4 usable and stable? I may want to check it out before deleting everything, now that I think about it. :)

---

### Post by justsomedude on 2008-03-12
> Is KDE4 usable and stable?

Well, that's debatable. In my opinion, it's not ready for everyday use, but other people might think differently. 

The developers say it will be production ready at version 4.1. But, go ahead and try, you can always remove it easily. Every KDE 4 package contains KDE 4 in it's name, so you can remove them easily in Synaptic.

I say it's worth a test drive. :-)

---

### Post by Nimaran on 2008-03-12
Okay thank you all very much.

---

### Post by Nimaran on 2008-03-12
OH NOO! I uninstalled the three things that popped up with a kde4 search, and I watched in horror as programs like kdm, kontact, and other such things including a bunch of other libs were removed. How to I get them back? I don't know all of what it removed, I'm scarred to touch anything else, much less restart, it help!!

---

### Post by justsomedude on 2008-03-12
1. Don't panic

2. > I uninstalled the three things that popped up with a kde4 search.

What three things exactly?

If it removed kdm-kde4 for example, it's allright. Or did it remove the normal kdm? 

You can check in adept if it is still installed.

---

### Post by Nimaran on 2008-03-12
See that's the thing, I don't remember.

*Cringes as baseball bat comes flying out of nowhere due to complete stupidity* 

I just remember seeing them scroll past. I went in and reinstalled kontact and kdm, so that should be okay, but I don't know what else it took out, when reinstalling those two things some more packages scrolled by that it was installing. So, it could have put everything back, but I'm not sure. I guess I'll just have to see if anything stops working next time I restart.

---

### Post by justsomedude on 2008-03-12
You can (re)install kubuntu-desktop and every default app should be there. 

Your personal configuration is not touched by this, so everything should be back to normal.

If you are missing some apps not included with the default install, they're just one apt-get away if worse come to worse.

Take a look:
[IMG]http://i25.tinypic.com/2iuumg8.png[/IMG]
The package dolphin is your default Dolphin, dolphin-kde4 is KDE 4s Dolphin. You can savely remove packages like this.

I hope I didn't create confusion, it was not my intention. If I did, sorry.

---

### Post by Nimaran on 2008-03-12
Oh no, your help was great. I think I got it working. Again thank you so much. Oh, I responded to your music management thread. I found a bookmark script for Amarok tell me if that is what you wanted.

---

### Post by justsomedude on 2008-03-12
Have you installed kubuntu-desktop?

If not, do so. It will install every missing package from your default KDE. Just to make sure.

It might also reinstall packages you uninstalled before, you can remove them afterwards.

If everthing is still in place, installing kubuntu-desktop will do nothing at all.

> I found a bookmark script for Amarok tell me if that is what you wanted.

Wow, if that works, you are my personal hero. :) I'll check it out now...

---

### Post by Nimaran on 2008-03-12
Wow, I did it and it worked great, a few other random things had gone missing and it put them all back. Thanks again. I hope that bookmark thing works for you.

---

