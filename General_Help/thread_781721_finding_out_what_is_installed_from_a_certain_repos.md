---
title: "finding out what is installed from a certain repository"
date: 2008-05-04
forum: General Help
---

### Post by purpleidea on 2008-05-04
Hi,
I'd like to do some house cleaning; in particular i'd like to start removing a lot (if not all) of the non-free components from my installation.

What I'd like to do is figure out how to list all the packages that are installed from a particular repository. I usually use aptitude when I can.

It would be nice if something along the lines of:

aptitude show-installed-from multiverse

would output the installed packages, and then the installed due to dependency...

cheers!
_J

---

### Post by chrisccoulson on 2008-05-04
What you can try is to disable the software sources that you don't want to use anymore, then use Synaptic's 'Local or Obsolete' filter (Status -> Installed (local or obsolete)). This will list all packages that were installed from the repositories you disabled.

I'm not sure how to do this with aptitude though.

---

### Post by purpleidea on 2008-05-04
> **chrisccoulson said:**
> What you can try is to disable the software sources that you don't want to use anymore, then use Synaptic's 'Local or Obsolete' filter (Status -> Installed (local or obsolete)). This will list all packages that were installed from the repositories you disabled.

I'm not sure how to do this with aptitude though.
Hey,
yeah I suppose I could do that.
the problem is that I can't do it on machines without X (eg: servers)
and the second problem is it's sort of a hack. Thanks for the good tip though!
Actually, in synaptic I just found an -origin- search which lets you sort by repository... not bad...
Don't suppose you (or someone else) knows of a dpkg way or something? I know there is a dpkg --list but not with a repository parameter that i know of.

ideas?
_J

---

