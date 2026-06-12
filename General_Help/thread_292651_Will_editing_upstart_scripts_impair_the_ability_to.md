---
title: "Will editing upstart scripts impair the ability to upgrade later?"
date: 2006-11-04
forum: General Help
---

### Post by ranarion on 2006-11-04
I'm interested in editing upstarts boot configuration, as I'm on a laptop and would like to experiment with event-driven starting of services.

Would editing upstarts configuration likely impair my ability to upgrade to feisty later?

---

### Post by BoneKracker on 2006-11-14
I don't know, but since nobody else answered...

I wouldn't think so.  The set of upstart jobs released with Edgy mimic sysvinit runlevels (in fact, they call the existing runlevel scripts).  I gather that by Feisty, upstart will include a set of independent jobs, hopefully capitalizing to some degree on its event interface.

You may want to consider backing up the existing set of scripts before monkeying with it, jotting down the changes as you make them so you can roll them back, and possibly backing up your modified scripts so they don't get overwritten by an update.

[http://upstart.ubuntu.com/doc/getting-started.html](http://upstart.ubuntu.com/doc/getting-started.html)

Edit:
Oh, and follow up with what you tried and how it worked out.  I am curious as to how people envision using this.

---

