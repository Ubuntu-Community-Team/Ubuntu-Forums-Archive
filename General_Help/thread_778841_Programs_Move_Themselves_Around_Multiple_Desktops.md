---
title: "Programs Move Themselves Around Multiple Desktops"
date: 2008-05-02
forum: General Help
---

### Post by armware on 2008-05-02
details: kde 3.5.9, kubuntu 8.04, 8 desktops

I have firefox opened in desktop 1, and akregator in desktop 2. I'm in akregator and I click a link. Firefox gets moved to desktop 2, when I'd rather it do nothing, but I cannot figure out how to change this.
BTW, this isn't just firefox doing it, kopete windows do it, too, leading me to believe it's a kde action/feature. 

How can I get my programs/windows to stay where I put them?

---

### Post by armware on 2008-05-20
a similar issue is when i'm launching a program that takes a bit to load up (aptana) in one desktop, then switch to another, when aptana is loaded it moves itself to the desktop i'm in.

how can i get a program to stay in its desktop until i specifically move it elsewhere? this is getting really annoying.

---

### Post by armware on 2008-05-22
oh c'mon. there HAS to be an option for this somewhere.

---

### Post by vom on 2008-06-11
I want to confirm this as well.  For the longest time I have had specific desktops where I run various apps (i.e. FF in 2 and Akregator in 3 (total 6)).  It seems that as of Hardy, FF follows the 'active' window i.e. Akregator, Kopete etc.  Kind of defeats the purpose of having multiple desktops.

---

### Post by vom on 2008-06-11
I had FF set as the default browser in KDE.  I went into akregator settings and hardcoded this to it's (greyed out) default of firefox %u and now this behavior has stopped.  I think we're screwed on kopete though, as I dont remember it having a static config for browser.

---

### Post by armware on 2008-10-07
seems to be a bug, but there also seems to be some confusion/conflict as to where the bug is, firefox or the window manager. bug reports have been filed at with all three, so it should be a matter of time.

---

### Post by armware on 2008-10-07
i wanted to try your suggestion, vom, but it just didn't seem universal enough (kopete still suffered, as you stated).

so what i came up with was to use kwin's application/window settings.

in firefox, right click the title bar->advanced->special application settings->geometry

i set mine to force it to desktop 1, as that's what works perfectly for me.

---

