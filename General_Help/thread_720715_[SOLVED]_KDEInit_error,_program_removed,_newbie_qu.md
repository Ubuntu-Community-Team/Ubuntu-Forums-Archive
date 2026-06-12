---
title: "[SOLVED] KDEInit error, program removed, newbie question"
date: 2008-03-10
forum: General Help
---

### Post by HousieMousie2 on 2008-03-10
Hi,

I am getting a message that says KDEInit can not load/launch or find gDesklets... which makes sense since I uninstalled it.  My question is how do I go about telling KDEInit not to try to load gDesklets?

I tried searching here and through Google, but all I am finding is situations where they want KDEInit to load the program in question, so the solutions offered are towards that end... not what I need.

I was only using gDesklets for Good Weather, but I like Liquid Weather through SuperKaramba - Desktop Widgets better and I can't recall what steps I took to set up gDesklets in the first place.

Also, is it okay to delete the .gdesklets folder that was left behind in my Home Directory?

Thank you for your time!



Kubuntu - Gutsy Gibbon - i386 - Fully updated/upgraded

---

### Post by walsh416 on 2008-03-10
You can definitely delete the folder but in order to completely get rid of screenlets, go into System->Administration->Synaptic Package manager and search for "screenlets" and uninstall anything to do with it.

---

### Post by HousieMousie2 on 2008-03-10
walsh416

Screenlets was not installed... lol obviously, can't uninstall it.  gDesklets is not listed as installed either.

Other ideas?

---

### Post by HousieMousie2 on 2008-03-21
Found a solution...

Remove it from Autostart directory, in .KDE, in my Home folder.

[http://www.linuxforums.org/forum/linux-newbie/104886-kdeinit-edit-start-items.html](http://www.linuxforums.org/forum/linux-newbie/104886-kdeinit-edit-start-items.html)


Seems simple enough. lol

Even seems to work too.  :-)

---

