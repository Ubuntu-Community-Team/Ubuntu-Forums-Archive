---
title: "Evolution annoying bug"
date: 2007-08-27
forum: General Help
---

### Post by deep-z on 2007-08-27
Evolution 2.10.1 frequently produces a following error:
Error while Storing folder 'Inbox'. Summary and folder mismatch, even after a sync".

Allready tried all possible solutions (removing index files, exporting and importing mails from mbox format), but no luck to get rid of this annoying error.
There are lots of people getting this error for a long time, but no working solutions so far...
And most of all what sucks is that after deleting index file, all messages, wich are flaged as important, loses their flags...

Maybe someone can come up with some new information regarding this stuff?.... :mad:

---

### Post by gobbles414 on 2007-08-27
Hey deep-z,

Have you posted this bug on the [Launchpad]("https://launchpad.net/ubuntu") website? That is a good place to discuss Ubuntu bugs.

---

### Post by deep-z on 2007-08-27
This bug is there allready, but no working solutions yet:
[https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/27014](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/27014)

Notice the bug submission date: 2005-12-13 ... quite long time for finding a fix for the problem, I think...

There's a new version of Evolution (2.10.2), but it's available only for Gutsy at the moment.

---

### Post by gobbles414 on 2007-08-27
Wow! I guess that I'm lucky to have never encountered this bug before. I don't know what to suggest.

---

### Post by deep-z on 2007-08-27
Maybe the problem is with Evolution startup messages index checks (or index rewriting), while at the same moment new mails are arriving and therefore not having proper access to message index (mail counts and status in Inbox by example). I have noticed, that this bug appears the most when Evolution is started and there is a new mail on server to download.

---

### Post by deep-z on 2007-08-27
This bug lives since 2001... (!!)
I have tried every solution I could find. Nothing helps.

---

