---
title: "gnucash won't start"
date: 2013-02-13
forum: General Help
---

### Post by laytek on 2013-02-13
Hi all,

I am using 10.04 Lucid, with gnucash installed. Today, it is refusing to start, showing the following error messages:

<unnamed port>: In procedure primitive-load-path in expression (primitive-load-path name):
<unnamed port>: Unable to find file "slib/init/guile.init" in load path

All was fine when I last used gnucash, now?

Any ideas?

Thanks, Alan

---

### Post by laytek on 2013-02-14
To answer my own question, I removed guile-1.6-libs using Synaptic. That also removed gnucash. I also removed gnucash-common. I then reload gnucash, which of course loaded all dependencies. The program is now operating normally, and it doesn't appear that I have lost any data.

What happened?

---

