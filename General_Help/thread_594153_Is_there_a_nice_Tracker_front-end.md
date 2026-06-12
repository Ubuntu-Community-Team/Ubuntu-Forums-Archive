---
title: "Is there a nice Tracker front-end?"
date: 2007-10-27
forum: General Help
---

### Post by Mr. Picklesworth on 2007-10-27
I really, really like Beagle's search front-end in GNOME. It is smooth and organized, and it doesn't require me pressing any more buttons to begin searching. It has a tidy way of showing me the contents of files that are related to my search, and some nice text formatting.

However, for everything other than the front-end, I currently prefer Tracker. The only problem is that tracker-search-tool is dumb!
Firstly, it has a completely absurd page flipping thing to go through search results. Why can't it just output everything in one list and have me use the scroll bar? (Particularly silly is that there is indeed a scroll bar, and it often must be used to scroll by tiny ammounts).
Even with this page flipping thing (which should, arguably, be present to permit room for a tidy interface), the Tracker Search Tool looks very cluttered because of how it presents the content of documents. Ellipsis' are everywhere :(

My need is probably obvious at this point:
Is there a nicer, more Beagle-ish, search front-end that works with Tracker?

---

### Post by jamiemcc on 2007-10-27
> **Mr. Picklesworth said:**
> I really, really like Beagle's search front-end in GNOME. It is smooth and organized, and it doesn't require me pressing any more buttons to begin searching. It has a tidy way of showing me the contents of files that are related to my search, and some nice text formatting.

However, for everything other than the front-end, I currently prefer Tracker. The only problem is that tracker-search-tool is dumb!
Firstly, it has a completely absurd page flipping thing to go through search results. Why can't it just output everything in one list and have me use the scroll bar? (Particularly silly is that there is indeed a scroll bar, and it often must be used to scroll by tiny ammounts).


We will support this in the near future - probably need to be an upper limit to prevent TST consuming tons of memory though if you retrieved 100,000 hits say (might simply set paging to 100 instead of 10)

> 
Even with this page flipping thing (which should, arguably, be present to permit room for a tidy interface), the Tracker Search Tool looks very cluttered because of how it presents the content of documents. Ellipsis' are everywhere :(


resize window to get rid of ellipses in the metadata tile
next version coming any day will support better resize of results window to help prevent ellipses

---

### Post by Steveway on 2007-10-27
You can try catfish.
It's pretty nice and even works with several different backends.

---

### Post by LuxeSaber on 2007-11-05
> **Steveway said:**
> You can try catfish.
It's pretty nice and even works with several different backends.

Thank you so much! I did not know about catfish and now catfish and I are best friends!

---

### Post by michaelzap on 2007-11-05
OK so I got excited and installed Catfish via Synaptic, but it only offers me find and slocate methods (not Tracker). The Catfish website doesn't seem to have any usage info at all, and I can't find anything else out there. How can I get Tracker results to show in the Catfish frontend?

---

### Post by Steveway on 2007-11-06
Do you have tracker-search-tool installed?
I can choose tracker-search in catfish.

---

### Post by michaelzap on 2007-11-06
> **Steveway said:**
> Do you have tracker-search-tool installed?
I can choose tracker-search in catfish.

Yep. Tracker works fine on its own. It just doesn't appear as an option in Catfish.

---

### Post by Steveway on 2007-11-06
No I mean this: [apt:tracker-search-tool]("apt:tracker-search-tool")

---

### Post by michaelzap on 2007-11-06
> **Steveway said:**
> No I mean this: [apt:tracker-search-tool]("apt:tracker-search-tool")

According to Synaptic, I already have that package installed.

---

### Post by Steveway on 2007-11-07
Well, I checked my repositories for everything trackerrelated that I have installed.
Just look if you are missing any of these packages.
libtrackerclient0
libtracker-gtk0
tracker
tracker-search-tool
tracker-utils
That should be all.

---

### Post by michaelzap on 2007-11-07
Thanks. I was missing the tracker-utils package. Once I installed that I could use Tracker via Catfish.

---

### Post by Gumper on 2007-11-20
I'm trying to get Catfish to work with tracker in my Kubuntu installation without much success. I have all the packages installed that were listed earlier, it just doesn't seem to work. I'm able to select 'tracker-search' but it doesn't find anything. If I search for the same thing using the regular tracker GUI it will find all kinds of things. 

Does anyone have any ideas why it's not working? Could it be because I'm using KDE?

---

### Post by Endolith on 2008-05-14
> **Gumper said:**
> I'm trying to get Catfish to work with tracker in my Kubuntu installation without much success. I have all the packages installed that were listed earlier, it just doesn't seem to work. I'm able to select 'tracker-search' but it doesn't find anything. If I search for the same thing using the regular tracker GUI it will find all kinds of things. 

Does anyone have any ideas why it's not working? Could it be because I'm using KDE?

Same problem.  Did you figure it out?

---

### Post by MaindotC on 2008-05-14
I'd never understood what a tracker was until I read this thread.  I'd heard of it, and I'd seen that thing that installs in the desktop toolbar by default - sort of looks like scribbling with a C on the end of it - but never knew what it was or what it was for.  All because of Picklesworth.  Damn you, Picklesworth!

---

