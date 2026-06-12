---
title: "administration question"
date: 2007-02-13
forum: General Help
---

### Post by idrifter on 2007-02-13
Hello all,

I'm a network administrator in a mostly Windows environment but I would like to start using Linux/Ubuntu for a few projects.  I have a decent working knowledge of Linux from some courses that I took in college but I'm by no means a guru.  One thing I have been wondering about is how to handle updates.  Is it safe / recommended to just make a quick script to run apt-get and have cron run that every night?  What happens if I customize a config file in /etc and that package gets upgraded?  Do I need to worry about my changes getting clobbered?

Thanks

---

### Post by Ramses de Norre on 2007-02-13
Config files aren't altered by upgrades, so your own changes will remain.
Having all packages automatically updated seems like a risk however, sometimes broken packages get uploaded (and are fixed a couple of hours later). A few days ago there was a thread here from a guy who'd set up apt-get to check daily for upgrades and mail them to him, he could then first check them before applying. You may want to search for that thread.

---

