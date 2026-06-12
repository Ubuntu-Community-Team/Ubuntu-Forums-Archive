---
title: "Let Firefox 2 and 3 share bookmarks"
date: 2008-04-29
forum: General Help
---

### Post by Orestez on 2008-04-29
So I was thinking that maybe I could have one bookmarks.html file, and use symbolic links to let both firefox 2 and 3 essentially use the same file.

However, I cant seem to find the actual bookmarks.html file for FF3. I have read somewhere that ff3 now uses a database to store its bookmarks... is that the case? Anybody here knows for sure what is the case? Tried searching, but didnt come up with anything useful. 

(the usual place, under ~/.mozilla/etc is used by ff2 it seems)


Thx in advance,
Orestez

---

### Post by z0mbie on 2008-04-29
Firefox 3 hasn't started using Weave. Mozilla's Weave is still under development. You can probably find the bookmarks in a directory similar to this one:

/home/YOURUSERNAME/.mozilla/firefox/d7p751vi.default/bookmarks.html

---

### Post by Orestez on 2008-04-29
Yes, I checked there. As I (maybe badly) explained in my first post, thats where firefox 2 seems to store its bookmarks. Just to clarify, I have FF2 and FF3 installed at the same time.

---

### Post by ajgreeny on 2008-04-29
Have you tried the firefox add-on which syncs bookmarks across all your firefoxes on all and sundry operating systems.  Can't remember exactly the name of it, nor if it will work in FF3, but it's worth looking into.

---

### Post by Orestez on 2008-04-29
Yes, thanks for the suggestion. I believe its called foxmarks or something, but its not exactly what I was looking for, since I only really want to syncronise the bookmarks locally on my computer. I might try it regardless tho, as a kind of workaround.

---

### Post by ksauber on 2008-04-29
Orestez,

You indicated that you have sucessfully don't something I'm having problems with - that is, installing Firefox 2.

I've installed it twice now, and the start icon in Applications -> Internet says "Firefox 2 Web Browser", but clicking on it just brings up Firefox 3 again.

Can you help?
Thanks!

---

### Post by Orestez on 2008-04-29
> **ksauber said:**
> Orestez,

You indicated that you have sucessfully don't something I'm having problems with - that is, installing Firefox 2.

I've installed it twice now, and the start icon in Applications -> Internet says "Firefox 2 Web Browser", but clicking on it just brings up Firefox 3 again.

Can you help?
Thanks!

Yes, that happened to me at first as well... I noticed that, when Firefox 3 already is running, and you try to start Firefox 2, FF3 will start.

However, when Firefox3 isnt running, Firefox 2 starts up just fine. At least thats how it is with me. 



On the note of FF3 bookmarks, there is a file in /etc/firefox-3.0/profile, but it doesnt contain my bookmarks...

---

### Post by chrisccoulson on 2008-04-29
Firefox 2 and 3 will not share bookmarks, as FF3 uses a sqlite backend for storing bookmarks (whereas FF2 uses the old bookmarks.html file)

---

### Post by Orestez on 2008-04-29
Thanks for the confirmation... sucks tho :(

---

