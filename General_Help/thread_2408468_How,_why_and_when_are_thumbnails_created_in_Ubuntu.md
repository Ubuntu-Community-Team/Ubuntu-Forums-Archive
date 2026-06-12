---
title: "How, why and when are thumbnails created in Ubuntu 16.04?"
date: 2018-12-19
forum: General Help
---

### Post by krylov2 on 2018-12-19
I need to do some recover work for the Document Viewer (Evince) and the thumbnails in ~/.cache/thumbnails/large appear to contain the necessary information. However, I need to know the rule of their creation. Are they created every time I open a document in some application (Evince or internet browser)? Are they ever deleted or are they kept on the hard drive forever?

---

### Post by ajgreeny on 2018-12-19
I am not certain if this is Xfce4 specific, ie Xubuntu, but the rules for thumbnail creation in that are all held in **/etc/xdg/tumbler/tumbler.rc**

Have a look in your version, if it exists, and you may be able to figure out what you want, though I'm afraid I did not fully understand what you want to do with thumbnails, or how you think they may help you recover anything.

Tell us in more detail and we may have other possibilities for you to try.

---

