---
title: "How to undo an update via Update Manager"
date: 2008-06-25
forum: General Help
---

### Post by mempman on 2008-06-25
Is it possible for an Update Manager update to be undone (i.e. revert back to the software setup before the update)?

---

### Post by sdennie on 2008-06-25
I'm not aware of a way.  What specifically are you trying to revert?

---

### Post by mcduck on 2008-06-25
No, the Update Manager only does updating..

For all other package management tasks you need to use Synaptic (in System/Administration/Synaptc Package manager).

You should be able to downgrade your package with Synaptic, but remember that you also have to pin the version, otherwise the package management will continuosusly keep on trying to update it to the latest version.

(of course it all depends on what package you are talking about, the more integral part of the system that package is the more likely you'l run into probelms.)

---

### Post by llama320 on 2008-06-25
I'm not sure if this is what you're looking for, but i'll try to lend some help

first to find the package you want to un-update, go to /var/log/dpkg.log

Once you've found the package, go into synaptic and search for it
You might be able to then go to Package > Force Version... and change back to the version pre-update

That said, I just checked a few of my most recently updated packages in synaptic and the Force Version option was grayed out for all of them, so I'm not entirely sure how much luck you'll have, but I figured I'd add in my 2 cents

Good Luck

---

