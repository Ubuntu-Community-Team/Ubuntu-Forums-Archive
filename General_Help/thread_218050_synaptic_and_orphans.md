---
title: "synaptic and orphans"
date: 2006-07-18
forum: General Help
---

### Post by wifiabc on 2006-07-18
Referring to this article:
[http://www.psychocats.net/ubuntu/aptitude]("http://www.psychocats.net/ubuntu/aptitude")

Would using synaptic have a similar problem as using apt-get when it comes to leaving orphans?

---

### Post by jvdowney on 2006-07-18
No matter how it's removed, there will often be some orphaned library files left. I recommend getting gtkOrphan (from Synaptic). It's the GUI form of deborphan, and a little friendlier for me, anyway. There is an option at the bottom that lets you select only orphans from removed packages - that way you don't have to worry about deleting optional libraries that may still be needed by some programs.

---

### Post by mlind on 2006-07-18
Yes, I believe synaptic is just front-end for apt-get, as is update-manager.
deborphan and debfoster will help you to get rid of orphaned packages, those that aptitude would normally remove.

---

### Post by wifiabc on 2006-07-18
Thanks.

---

### Post by Sef on 2006-07-18
> Yes, I believe synaptic is just front-end for apt-get, as is update-manager.

You are correct.

> deborphan and debfoster will help you to get rid of orphaned packages, those that aptitude would normally remove.

When installing packages it is best to use aptitude instead of apt-get.  Makes removing packages a lot easier; it will do it instead of leaving them behind.

sudo aptitude install package-name

---

### Post by aysiu on 2006-07-18
> **jvdowney said:**
> No matter how it's removed, there will often be some orphaned library files left. That's not true. If you install the application with *aptitude* and remove it with *aptitude* there are no orphaned libraries.

---

### Post by wifiabc on 2006-07-18
Is there a version of synaptic that use aptitude instead of apt? Are there any GUI frontend for aptitude?

---

### Post by aysiu on 2006-07-18
> **wifiabc said:**
> Is there a version of synaptic that use aptitude instead of apt? Are there any GUI frontend for aptitude?
None that I know of.

*aptitude* has its own text-based GUI frontend for itself.

Type ```
aptitude
```

---

### Post by cssutto on 2006-07-18
I have looked at aptitude and it scares the hell out of me.

For instance, the first thing I see when I open it is "empty this list".

What does that mean?

And "forget new packages"?  I have no ides.

What I would like to know is what to do the first time I use aptitude to get it synced with what I have done using synaptic.

Then I would assume that from that time on, one would have to use aptitude every time so that it would know what has been and not been done.

CSSJR

---

