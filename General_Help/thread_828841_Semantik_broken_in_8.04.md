---
title: "Semantik broken in 8.04?"
date: 2008-06-14
forum: General Help
---

### Post by jurymast on 2008-06-14
How come Semantik is in the repositories, 'installable' and yet doesn't install properly?  What gives? :confused:

---

### Post by jurymast on 2008-06-14
I've got in touch with the developer.  Hopefully something will get accomplished by this.  Will get back if I hear anything.

---

### Post by jurymast on 2008-06-14
He told me to get in touch with the maintainer.  You're supposed to check out [Launchpad's Semantik page]("https://launchpad.net/ubuntu/+source/semantik/+bugs") first, though, so I did.

---

### Post by jurymast on 2008-06-17
The maintainer got back to me.  To get Semantik to run (and it's worth it!), in Terminal type:

export PATH=$PATH:/usr/lib/kde4/bin
semantik

---

