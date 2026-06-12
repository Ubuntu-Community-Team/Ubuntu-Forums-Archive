---
title: "Where to place apps that don't need installing?"
date: 2017-02-12
forum: General Help
---

### Post by javierdl on 2017-02-12
Programs like Blender, SuperTuxKart, etc. Programs like this will simply expand off of a compressed file into a folder, basically where ever you choose. And will run from that location.
So far I have been putting them into an Applications folder I create in Home. But I believe I read from a developer, to put them in "opt" instead. Is there an actual advantage in going with the latter choice? Or it really doesn't matter?

Thanks guys,

JDL

---

### Post by The Cog on 2017-02-12
/opt is a traditional place to install optional software like that. But it depends who is going to use it.

If multiple users are going to run the software then it should probably be installed in /opt and changed to be writable only by root (i.e. root should do the install). This means that users don't have to try and run software from other users' home directories, along with all the doubts about whether they have access at all, and whether they trust the other user not to make malicious changes.

If the software is for use by a single user then I don't think it matters so much. Issues such as whether it gets backed up as part of the user's home folder, which partition has most free space, and whether the user wants to  do updates without needing root permissions may be the deciding factor.

---

### Post by javierdl on 2017-02-12
This is exactly what I was expecting!
Thank you so much for that The Cog :)

J

---

