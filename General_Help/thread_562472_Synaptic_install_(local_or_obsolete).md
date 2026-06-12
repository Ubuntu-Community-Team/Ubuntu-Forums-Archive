---
title: "Synaptic: install (local or obsolete)"
date: 2007-09-28
forum: General Help
---

### Post by OldTimeTech on 2007-09-28
I just upgraded to Feisty:

When I went to check synaptic, I found I had a new line that says install (local or obsolete).

I did a search on this in google and on the forums.  Some say you can get rid of these they aren't important, some say to force installation and others seem to be just to far over my head to understand.

I checked properties these are all programs that are supposed to be the lastest and used in Feisty...

acroread
acroread-escript
amorak
amorak-xine
blender
bmp-docklet
clamav
clamav-base
clamav-daemon
more clamav designations
easytag
flashplayer mozilla
these just go on and on....

so my first question is: what does the install (local or obsolete) mean, and I've checked synaptic home page without getting my question answered.

second question is what do I do with all these programs?

Ahead of time, thanks for any help!

---

### Post by por100pre1 on 2007-09-28
If you installed downloaded packages or installed packages from repositories that you eventually removed or disabled from your sources.list; they will appear in that section. It means that they are not form any of your enabled repositories, they were installed by yourself (local), or are no longer in the repos (obsolete).

EDIT: The answer to your second question is to keep them if they work fine. However if you prefer to use the repository versions (if they are available) you can click the package and press Ctrl+E to force install the version from the repositories. Hope it helps. :)

---

### Post by OldTimeTech on 2007-09-28
Your first answer is interesting, because I've not downloaded or installed any new packages either from the repositories or from anyplace as I just upgraded to Feisty and all of these are suppose to be Feisty programs according to properties.

I will try the Ctrl+E to force the install.

Thanks for information.

---

### Post by kerry_s on 2007-09-28
it means they have been updated or replaced and you don't need them.
but if you installed anything using "sudo dpkg -i" you need to lock those 1's those are the programs that you installed that were not in the repo.

---

