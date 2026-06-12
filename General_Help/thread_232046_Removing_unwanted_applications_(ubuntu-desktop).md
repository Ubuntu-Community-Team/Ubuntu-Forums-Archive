---
title: "Removing unwanted applications (ubuntu-desktop)"
date: 2006-08-08
forum: General Help
---

### Post by s_g_robertson on 2006-08-08
Hello,

I wonder if anyone can help me with what I think should be a very simple question but I've got myself confused.  I'm trying to get rid of things that I don't use on one of my ubuntu machines that is mainly just used as a server.  I do however at this stage want to keep Gnome.

For example I don't need openoffice on it.  If I try to remove it using aptitude I get a message saying

"ubuntu-desktop depends on openoffice.org2"

Can I remove openoffice with breaking things?

Thanks.

Stephen

---

### Post by az on 2006-08-08
The ubuntu desktop package is just a metapackage.  You can remove it safely and still happily run your system.

You should be aware that it is needed to upgrade from one release to another, so you may have to put it back to upgrade to the next release of Ubuntu.

---

### Post by s_g_robertson on 2006-08-08
Thanks for the very quick reply.

Stephen.

---

