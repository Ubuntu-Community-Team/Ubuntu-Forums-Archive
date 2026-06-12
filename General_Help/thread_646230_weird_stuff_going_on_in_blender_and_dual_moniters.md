---
title: "weird stuff going on in blender and dual moniters"
date: 2007-12-20
forum: General Help
---

### Post by anfractuosities on 2007-12-20
I just finished getting my second moniter to work using the Big Screen technique for ati x1600,
I wanted to do this for using blender, except, now, when I run blender, I cannot use any of the menus.  None of the respond.  I can move the default block around, but I can;t even bring up the tool kit.

Any ideas?

IT happens even if I change the resolution back too.

---

### Post by anfractuosities on 2007-12-21
bump.

SOLVED

I edited this line out of my xorg.conf
```

Option "EnablePrivateBackZ" "yes" #Enable 3d support <= May Not Work
```

---

