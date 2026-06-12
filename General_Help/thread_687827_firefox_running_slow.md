---
title: "firefox running slow"
date: 2008-02-04
forum: General Help
---

### Post by nofear07 on 2008-02-04
All since Sunday firefox has been running slow.  Most pages in general, but I really notice it on gmail, yahoo and google.  Does anyone know what is causing this?

I uninstalled then reinstall flashplugin-nonfree.  Also installed gnash, gnash-common, mozilla-plugin-gnash  And I still have the same issue.

Gmail when loading after login takes 30 seconds plus.  Before Sunday (yesterday) it would take maybe 5 secs, and it runs at 100% cpu usage.  Looking at /var/apt/log/ sunday there was an upgrade: app-install-data-commercial 8.3

Should I try downgrading that ?
Attached is a screenshot and the font's and widgets started being funky when this happened.

Any thoughts?

---

### Post by rfruth on 2008-02-04
What changed (any new extension / themes etc) ?

---

### Post by nofear07 on 2008-02-04
nothing on firefox side...
The only other possible thing that had changed was I installed codeweavers crossover office on Thursday and setup some office apps on Friday that downloaded and installed new fonts.

---

### Post by jan quark on 2008-02-04
the gnash and flash might hinder each other, there was such a thread somewhere

I would use only one of them

and also give another web browser a try like for example kazehakase
which I use and I am quite pleased with the speed and simplicity

---

### Post by rfruth on 2008-02-04
another browser (even if just for testing) = good idea OR new/different Firefox profile (.mozilla)

---

### Post by y-lee on 2008-02-04
> **jan quark said:**
> the gnash and flash might hinder each other, there was such a thread somewhere

I would use only one of them

yep not a good idea.

Clean your history up, cookies and all that as well as cleaning up all your downloads in your FF download manager. See if that helps.

Create a new profile and try that
```
firefox -P
```  If so there is something in your profile causing the problem.


I usually advice trying to fix a problem rather than installing another program but [Swiftweasel]("http://swiftweasel.tuxfamily.org/") is another option, it is really firefox just compiled for speed. Easy to install as they have debs. I use it  and it is faster, when you install it it copies your firefox profile. I lost some of the options in my add ons but the add ons were there. I just had to reset the options. It also seemed to use firefoxs about:config file :)

---

### Post by manimal347 on 2008-02-04
Epiphany is a good pick. It's much more professional then Kazenhakaze, and is also a lot more stable than Firefox/Iceweasel, which both, frankly, are slow and cantankerous.

---

### Post by sports fan Matt on 2008-02-04
Im planning to run epiphany till wednesday of this week then decide:)

---

