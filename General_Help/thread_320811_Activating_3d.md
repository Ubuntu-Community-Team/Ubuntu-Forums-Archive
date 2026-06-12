---
title: "Activating 3d"
date: 2006-12-17
forum: General Help
---

### Post by sagasha on 2006-12-17
How do you activate 3d in your config? I was running Suse 10.2 and it's an option in setting up your video card (mine does support it)

---

### Post by dcstar on 2006-12-18
> **sagasha said:**
> How do you activate 3d in your config? I was running Suse 10.2 and it's an option in setting up your video card (mine does support it)

**glxinfo** will tell you if Direct Rendering is available.

---

### Post by pay on 2006-12-18
A simplier way is ```
glxinfo | grep rendering
```

---

### Post by steve.horsley on 2006-12-18
Open this page [http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy) and search for "graphics driver".

---

