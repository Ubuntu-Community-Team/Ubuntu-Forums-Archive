---
title: "Firefox 2.0.0.2"
date: 2007-02-28
forum: General Help
---

### Post by Tantalus90 on 2007-02-28
Anyone else getting Firefox crashes since the Update to 2.0.0.2 ?

I listen to pandora in a minimised window but no probs before the update,

Today it seems every time i try to post on a forum all firefox windows close

---

### Post by i.am.canadian on 2007-02-28
I'm having similar problems.  I can't go to newsforge any more without my browser crashing.  I really don't know what it is, unless it is causing a problem with flash now?  Just my guess.

---

### Post by cookfromfrozen on 2007-02-28
I'm not having any problems with it, but I noticed on Digg that quite a number of people were getting crashes, especially with Java.  I don't have Java installed so I can't test that.

---

### Post by Tantalus90 on 2007-02-28
Thanks , have a java program running often though not always

Oh and i forgot, Skype :confused: 

Not sure I like skype but I have buddies want to get in touch so it is on a lot 

But whatever causes it , firefox is the only thing that dies

---

### Post by traneHead on 2007-02-28
Yepps, me too. Happend twice today since the upgrade, first time it froze up everything for 10 sec or so, making rhythmbox repeat like an old LP. The second time, just a few minutes ago, it froze X completely until gdm restarted.
Both times I was marking/selecting text in ff (which I just discoverd I tend to do a lot while reading..)
So, this is the second time upgrading ff turns out to be a quality downgrade... sad.
Has anyone filed a bugreport?

---

### Post by Tantalus90 on 2007-03-01
> Has anyone filed a bugreport?

No , mainly because I cant be specific about what is causing it

---

### Post by i.am.canadian on 2007-03-01
Hi all,

I seem to have fixed the problem on my computer.  It seems that it was a flash issue after all.  When I upgraded, it must have over written the changes I had made before.

edit /usr/bin/firefox so that the second last line (that is the last but one) now reads: ```
export XLIB_SKIP_ARGB_VISUALS=1
```

Then restart firefox and you should be good to go.

Cheers.

---

### Post by shimrah on 2007-03-02
Excellent!

I was getting a crash every time I right-clicked and attempted to "save link as". This fixed it right away.

Out of curiosity, what does that line mean?

---

### Post by Tantalus90 on 2007-03-03
Sorry :( , tried it and I am still getting crashes

---

### Post by i.am.canadian on 2007-03-03
I have no idea what it means, I certainly didn't come up with it.  It has something to do with the way flash in firefox passes the graphics to your video card (I think, someone will undoubtedly correct me).

If it didn't work, I'm sorry, but I don't know what would.  Maybe you are having a slightly different but similar problem.  My only advice would be to try and isolate what exactly is giving you the problems.

---

### Post by bazzer on 2007-03-04
Yep, I'm getting crashes every 2 mins with 2.0.0.2. So bad I'm back to Konqueror.:mad:

---

