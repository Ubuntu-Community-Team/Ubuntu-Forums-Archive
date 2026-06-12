---
title: "GNash unable to display video on YouTube?"
date: 2008-06-02
forum: General Help
---

### Post by D.Sync on 2008-06-02
I had chosen Gnash over Adobe Flash Player just to try out it's new feature. Btw, upon installing it videos on YouTube couldn't be viewed? Any solution for this?

How can I remove Gnash and install Adobe Flash Player instead?

---

### Post by Prospero2006 on 2008-06-02
open up the shell and do a sudo apt-get purge package-name

Or you could look in ~/.mozilla/..whatever for the plugins and delete it.

Or you could do this

```

locate plugins

```

That will also show you all your plugins directories. 
From that point you should be able to hunt it down and kill it!

Sorry, I got a little over-excited there :'*

---

