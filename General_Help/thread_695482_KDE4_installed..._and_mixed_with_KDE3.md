---
title: "KDE4 installed... and mixed with KDE3??"
date: 2008-02-13
forum: General Help
---

### Post by MadMage on 2008-02-13
Hi all.
I installed KDE4 from [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) gutsy repository. It works. Anyway, now I have some mixture of KDE3 and KDE4 when I open a KDE 3 session, for example:

if I run "konsole" from the "run command" it opens a KDE4 konsole, not KDE3 one! anyway, I can open kde3 konsole by typing "/usr/bin/konsole"

My KDE menu has some mixed entries, for example in "system" menu there are both konsole's (one of them is without the icon and is actually the kde4 one), I have two dolphin... etc

Why this happened? Is there a way to avoid this?

---

### Post by coolclassic on 2008-02-13
At present not all software has been upgraded to kde4. The install procedure has aloud you to have kde4 and be able to use kde3 packages and visa versa. You can have a pure kde4 by installing a kde4 pacific OS but you will find some packages missing.

---

### Post by PmDematagoda on 2008-02-13
Installing KDE4 with KDE3 is a bad idea since both KDE3 and KDE4 packages would be mixed together which would confuse the two KDE versions and cause them to have problems.

You can either:-
1) Remove KDE3 and it's packages and install KDE4 packages only.

2) Use Linux releases that utilise KDE4 by default such as OpenSuSE 11 or Kubuntu Hardy Alpha 3 and above.

---

### Post by MadMage on 2008-02-13
> **PmDematagoda said:**
> Installing KDE4 with KDE3 is a bad idea since both KDE3 and KDE4 packages would be mixed together which would confuse the two KDE versions and cause them to have problems.

You can either:-
1) Remove KDE3 and it's packages and install KDE4 packages only.

2) Use Linux releases that utilise KDE4 by default such as OpenSuSE 11 or Kubuntu Hardy Alpha 3 and above.

So... what's that repository for?

---

### Post by MadMage on 2008-02-13
> **PmDematagoda said:**
> Installing KDE4 with KDE3 is a bad idea since both KDE3 and KDE4 packages would be mixed together which would confuse the two KDE versions and cause them to have problems.

You can either:-
1) Remove KDE3 and it's packages and install KDE4 packages only.

2) Use Linux releases that utilise KDE4 by default such as OpenSuSE 11 or Kubuntu Hardy Alpha 3 and above.

And... above all, what's this link and announcement for?

[http://kubuntu.org/announcements/kde-4.0.1.php](http://kubuntu.org/announcements/kde-4.0.1.php)

---

### Post by PmDematagoda on 2008-02-13
While it is true that you can install KDE4 with KDE3 it still is more difficult and less reliable than using KDE4 stand-alone since KDE4 will display KDE3 applications and vice versa.

That announcement(in my opinion), is meant more to show a way of previewing KDE4 rather than having people completely switching to KDE4 for all their productive work because of problems which people can face such as the ones you are facing.

---

### Post by MadMage on 2008-02-13
> **PmDematagoda said:**
> While it is true that you can install KDE4 with KDE3 it still is more difficult and less reliable than using KDE4 stand-alone since KDE4 will display KDE3 applications and vice versa.

That announcement(in my opinion), is meant more to show a way of previewing KDE4 rather than having people completely switching to KDE4 for all their productive work because of problems which people can face such as the ones you are facing.

I'm sorry, but I do not agree with this. If I read an announcement that states "They install to /usr/lib/kde4 and can be installed alongside your existing KDE 3." I think that "alongside" means somewhere else.

Anyway, the "run application" probably use a PATH that is different to the environment PATH, do you know where to set it?

---

### Post by PmDematagoda on 2008-02-13
I am afraid I do not have much experience concerning that.

Also I have installed KDE4 on Ubuntu 7.10 myself and while it works well it still has quite a lot of glitches which I think could be caused by other conflicting packages and whatnot. 

So while you can install KDE4 alongside KDE3, it is always easier and more reliable if you keep them separate so that they do not interfere with one another.

---

### Post by Jimmy Johnson on 2008-03-28
From this page: [http://kubuntu.org/announcements/kde-4.0.php](http://kubuntu.org/announcements/kde-4.0.php) it says: "KDE 4 apps should appear in your KDE 3 K-menu or you can run a full session by selecting "KDE 4" from your login manager."

So I guess this is by design.

---

### Post by MadMage on 2008-03-31
> **Jimmy Johnson said:**
> From this page: [http://kubuntu.org/announcements/kde-4.0.php](http://kubuntu.org/announcements/kde-4.0.php) it says: "KDE 4 apps should appear in your KDE 3 K-menu or you can run a full session by selecting "KDE 4" from your login manager."

So I guess this is by design.

yes you are right: the mix in the K-menu is by design

BUT, why the "run application" runs the kde4 app instead of the kde3 one? (and how to change this behavior?)

---

