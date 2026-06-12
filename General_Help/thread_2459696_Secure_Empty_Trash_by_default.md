---
title: "Secure Empty Trash by default"
date: 2021-03-23
forum: General Help
---

### Post by Unguidedone on 2021-03-23
im a total nix user 4 life but i saw something that caught my eye: mac Secure Empty Trash feature

this could add a higher level of security then our current ubuntu trash system.  now keep in mind since its written for a mac the secure trash delete is 100% not implemented properly because you got 'those' people writing the software.  I think its a good feature to add into a file manager or does it already exist?

(also dont invoke bleach bit on ubuntu or shred or dd)  i want to know if there is a file manager with by default options to enable secure delete for items in trash.  if not where is a place where we can say "this is a good idea lets add it to the next LTS package"

---

### Post by TheFu on 2021-03-24
It wouldn't be hard to script ... using /dev/random and dd. ;)

This isn't an Ubuntu thing.  They take programs from upstream projects, so you should figure out which file manager you'd like to make the feature request from, then find their project page, then politely suggest it.  Suggestions with code that implements the desired feature have much more weight.  Otherwise, expect to wait until a developer on that project feels the "itch".  When I'm developing, I scratch my own itches first.

Of course, it would be worth checking whether the tool already exists in a later version.  Ubuntu tends to be 6-36 months behind the upstream projects current code.

One of the problems is that different file managers use different "Trash" subsystems and some don't use any, so where the already trashed files are located on disk needs to be discovered, then each block overwritten with random data and lastly the file deleted.  Just be certain your backups don't capture the location of the Trash Bin directory on your system, since getting old files out of backups would be something I'd try.

---

