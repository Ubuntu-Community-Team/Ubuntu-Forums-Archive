---
title: "Please Help.  Desktop reverted to default ubuntu 14.04"
date: 2015-09-17
forum: General Help
---

### Post by BakedCanuck on 2015-09-17
When I booted my computer this morning I was surprised to see that my desktop (launcher, wallpaper, unity tweaks, etc) had reverted to default.  Now changing anything on the GUI via system settings or unity tweak has no effect.  I can add programs to the launcher but they are removed after restarting.  My computer did shutdown last night because it ran out of power, I read in one post that that can corrupt the config/dconf/user file.  I removed the file but it didn't fix the problem.  I also tried resetting the unity desktop using
dconf reset -f /org/compiz/

setsid unity

This did not fix the problem either.  Any help would be greatly appreciated.

---

### Post by tshade on 2015-09-20
Maybe the filesystem is corrupt. You'll need to check it.

---

