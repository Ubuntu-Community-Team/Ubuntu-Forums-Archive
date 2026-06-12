---
title: "Setup program for users that need access to /var/log"
date: 2007-12-29
forum: General Help
---

### Post by berlinbrown on 2007-12-29
I downloaded a package the normal way (download, compile).  I installed it to the opt directory and hence it is setup under the root user.  How do I setup this application so that it can be used by other users beside root.  Eg. it attempts to write to /var/log, so I am assuming I need to put that application under a special group or something?

---

### Post by SOULRiDER on 2007-12-30
What application is that exactly? AFAIK the only way to do such thing is to run the app as root or to chmod the files/directories that are to be written

---

