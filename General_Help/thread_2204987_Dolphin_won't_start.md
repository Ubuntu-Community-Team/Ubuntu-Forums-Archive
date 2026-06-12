---
title: "Dolphin won't start"
date: 2014-02-11
forum: General Help
---

### Post by Rob Sayer on 2014-02-11
So I installed Lubuntu 13.10 this morning (sounds like a blues song already) on my 1Gb netbook.  It's really fast.  There's more manual config but I expected that.  Had kubuntu 13.10 before, then mint 16 Mate, which is based on 13.10.

Did my mdm5sums, install went quickly and smoothly.  It's updated to the teeth.

But I installed my favorite file manager, Dolphin.  It won't run.  I expected it to start a bit slowly since it installs a bunch of KDE dependencies.  But that was more than a half an hour ago.

What gives?  Are there any resonably powerful file managers that *do* run in lubuntu?

---

### Post by Rex Bouwense on 2014-02-11
Of course.  PCManFM (which is the default file manager) runs quite well.

---

### Post by Rob Sayer on 2014-02-11
Of course?  OK.  I guess I'll get used to it.

---

### Post by vasa1 on 2014-02-11
> **Rob Sayer said:**
> ... But that was more than a half an hour ago.

What gives?  Are there any resonably powerful file managers that *do* run in lubuntu?

You mean that you waited for 30 minutes for Dolphin to start? Then what happened? You left out that part.

---

### Post by ant2 on 2014-02-11
Does it start if you try and launch it from a Terminal?

---

### Post by Rob Sayer on 2014-02-12
It never started, and I didn't try calling it from terminal yet.  I figured I'd try  PCManFM for a few days more before trying anything.   I used to use xfce for a time and this is way better than Thunar.  I despise Thunar.

I wasn't sitting there chewing my fingernails waiting for it either.  I was doing other things on the machine.

But now I can't resist ...

Tried Menu->Run.  It worked.

Then I closed it and tried to run it from the menu.  Nothing.

Looking at Task Manager, there are a number of kde library modules running (kactivitymanagerd, kded4, kdeinit4, klauncher).  No dolphin.  It opened from menu->run almost instantly.

Thanks for the responses.  Except the 1st one.

---

### Post by vasa1 on 2014-02-12
> **Rob Sayer said:**
> ...  I despise Thunar.
...
Thanks for the responses.  Except the 1st one.

It must be quite amusing to condemn software one is incapable of improving. And Thunar is meant to be a lighter "file manager" and consequently is less feature-full. And that causes you to despise it :) Fascinating.

---

### Post by Rob Sayer on 2014-02-13
So I tried setting default file manager to dolphin in preferences->default applications for LXsession.  This apparently has worked for others.  It didn't for me.

However, this brings up another issue.  The LXsession default screen does not fit on my 1024X600p netbook.  I grabbed a screenshot from a web page and it's missing the bottom line (the one that says widget 1), and it won't resize vertically.

This is more serious, and I'm going to start another thread ...

I can definitely live with the default file mgr until that's solved.

Edit:  found a workaround for too big windows that won't resize ... kludgy but it works.

Mind you, this desktop is SO fast on my netbook that I suspect I'll be willing to forgive a few rough edges.  I'm surprised ... I've been using ubuntu on my hardware for years and I've never tried LXDE until 2 days ago.

---

### Post by vasa1 on 2014-02-13
> **Rob Sayer said:**
> ...  The LXsession default screen does not fit on my 1024X600p netbook.  I grabbed a screenshot from a web page and it's missing the bottom line (the one that says widget 1), and it won't resize vertically.
...
Do you mean the screen in the lower image in [this link]("http://askubuntu.com/questions/362263/what-is-default-applications-for-lxsession-in-lubuntu-13-10")? In that case, it would be more helpful to refer to it as either *lxsession-default-apps* or *Menu* > *Preferences* > *Default applications for LXSession*.

---

### Post by Dennis N on 2014-02-13
> However, this brings up another issue. The LXsession default screen does not fit on my 1024X600p netbook. I grabbed a screenshot from a web page and it's missing the bottom line (the one that says widget 1), and it won't resize vertically.


Just one of the notorious "minimum-height" windows found here and there. By that I mean it can't be resized to less height (somewhere around 800 px, I think). Ingenious. It's not the only one like that. Solution is to "grab" the window by pressing and holding down the Alt key, and then press and hold down the left click mouse button while positioning the cursor over the window. You can then push the window up to see what lies below.

---

### Post by Rob Sayer on 2014-02-15
Yep, that works.  I'm still wrapping me head around the less integrated concept in LXDE.

I'm still a little concerned about being able to run dolphin from the menu.

However, this is on my netbook.  I don't really use it at home, mostly just for running around and jacking into hotspots.  I'm not sure I want to load the system up with too many dependencies.  This system is *fast*.

---

### Post by Rob Sayer on 2014-03-08
It'd be nice if someone could say why when I change the default file manager to dolphin in LXsession preferences, nothing happens.  I've searched the subject and found absolutely nothing.

At this point I'm seriously thinking of upgrading my netbook RAM and going back to kubuntu when 14.04 comes out.  Lubuntu support is definitely the worst of all ubuntu flavors.

---

