---
title: "Running a LAMP server on Desktop Edition"
date: 2007-11-20
forum: General Help
---

### Post by WonderCody on 2007-11-20
Would it be alright if I ran a LAMP server on the desktop edition of Ubuntu 7.10.  What features would I lose other than performance because of the GUI?

---

### Post by colo on 2007-11-20
That works just fine, there's no performance penalty you'd actually experience (unless you get thousand of hits a day on the httpd you're running). You won't lose any features, either. Just install apache2 and all the other goodies you need, and start right away.

I'd still recommend against running an internet-exposed production LAMP setup on a desktop machine. That just does not feel right. ;) It's perfectly OK for fooling around or doing development, though.

---

### Post by WonderCody on 2007-11-20
thanks!

---

