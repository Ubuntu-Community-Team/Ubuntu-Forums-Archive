---
title: "Feisty features in Edgy?"
date: 2007-04-26
forum: General Help
---

### Post by wyth on 2007-04-26
I tried to upgrade to Feisty and for a couple reasons, it just didn't work out. (Problems were posted [here]("http://ubuntuforums.org/showthread.php?t=419098") and [here]("http://ubuntuforums.org/showthread.php?t=422878"); in short, the radeon driver doesn't play well with my ATI 9000 (Radeon R250) card, shreds my screen on anything graphics-intensive or with any QT app like Amarok, fglrx isn't supporting my card in Xorg 7.2, and Network Manager refused to connect to the same secure networks that it did in Edgy.)

But there were a few things in Feisty I found very useful, especially the latest Gnome and OOo 2.2.  I tried installing OOo 2.2 on its own, but apt kept removing it on each update or instal of something new.  

So my question: Is there a way to get some of these latest application updates via repositories in Edgy?  I don't know if I'll ever be able to use Feisty, but some of those features I really liked.

---

### Post by wyth on 2007-04-26
*badabump*

---

### Post by justinjstark on 2007-04-26
It should be possible to add the main feisty repositories to edgy. Be careful: do not update afterwards or you will be back to running feisty.  Select the packages from feisty that you want and try to install them individually.  I can foresee some serious dependency problems but you can give it a shot.

I do the same thing only backwards.  Some packages worked better in edgy so I have an edgy repository in my feisty install and force the older edgy versions of some applications.

---

### Post by wyth on 2007-04-27
Justin, can I ask, did you just add the repositories, or did you change Feisty to Edgy in sources.list?

*Omaha, eh?  I was born there.  Many fond memories of the Henry Doorly; my aunt worked there, and got me and my brothers in to pet a juvenile tiger when it was knocked out for dental surgery... even at a year old, its paws were bigger than my head.*

---

### Post by justinjstark on 2007-04-27
Ah, Omaha.  It's a nice town but I can't wait to leave.  :)

I just added the one edgy repository.  It works well for me because all edgy packages are older than feisty packages so it doesn't auto-update anything but I can force old edgy packages.

If I were you, I would leave the edgy repositories alone.  Just add the feisty repositories that you need, install newer software, and remove the repository right away.  Let me know if it works.

Just be warned: there could be some serious compatibility issues between different versions of software.

---

