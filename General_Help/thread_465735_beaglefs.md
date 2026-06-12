---
title: "beaglefs???"
date: 2007-06-06
forum: General Help
---

### Post by hanzomon4 on 2007-06-06
I found beaglefs in the repos, what does it do?

---

### Post by hanzomon4 on 2007-06-06
Nobody?

---

### Post by EndPerform on 2007-06-06
> **hanzomon4 said:**
> I found beaglefs in the repos, what does it do?

```

fubar@scooby:/var/cache/apt/archives$ apt-cache search beaglefs
beaglefs - implements a filesystem representing a live Beagle query

```

Apt-cache will give you a brief idea of what a package does. :)

---

### Post by hanzomon4 on 2007-06-06
Yeah I read that but I don't know what that means. Is this like the trackerfs, or the Winfs?

---

### Post by hanzomon4 on 2007-06-06
I found news on OSnews.com [A Visual Look at BeagleFS]("http://www.osnews.com/comment.php?news_id=15256"). I guess I'll just have to try it out and see what happens...

This is clearer:> Not to be outdone, the always-busy and sadly-not-working-for-Canonical-anymore 
Jeff Waugh has uploaded Robert Love's latest gift to the 
world, '''beaglefs''' 1.0.3 . This allows you to take a beagle query and make 
it into a filesystem, to be mounted just like a CD or a hard drive partition. 
More information and shiny screenshots can be seen at Robert's blog, 

---

### Post by hanzomon4 on 2007-06-06
Neat, I tried it out.. 

Basically it lets you mount a beagle search. 

Ex: I run a beagle search to find all of my mp3 files by using this query "ext:mp3". With BeagleFS I can save the results as a virtual directory, a directory filed with sim-links to the actual files. The syntax is basically this "beaglefs query mount_point". So to make a virtual directory out of my ext:mp3 search I would do this "beaglefs ext:mp3 mp3dir".

---

