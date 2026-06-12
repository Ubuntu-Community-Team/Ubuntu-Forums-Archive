---
title: "Why are pdftotext and trackerd always running?"
date: 2007-10-21
forum: General Help
---

### Post by bpont on 2007-10-21
Since upgrading to Gutsy, I notice they are always running and eating resources.  What are they for and do I really need them running all the time?  If not, how do I turn them off?  Thanks.

---

### Post by cccccccc on 2007-10-21
The same problem here... 100% processor in use

---

### Post by javier_onaendia on 2007-10-22
Try disabling indexing. Go to System --> Preferences --> Indexing Preferences, you'll get a dialog box with several tabs. Try first unchecking everything just to see if cpu load goes down (it worked for me, but I had previously killed scrollkeeper-update process which was also eating a lot of cpu). Then you can start doing fine tunning checking indexing options one by one to see what happens...

---

