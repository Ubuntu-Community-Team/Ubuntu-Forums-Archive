---
title: "Where is .B.blend file? (Blender related)"
date: 2006-08-17
forum: General Help
---

### Post by bluntu on 2006-08-17
Anyone of you here who uses Blender knows where the .B.blend file is located in Ubuntu?

Tell me I'm blind cause I have spent all night trying to look for it and no luck. I know it's in my system but don't know where. I know for a fact that it's in my system because each time I run Blender my default setting is loaded.

---

### Post by christhemonkey on 2006-08-17
Try doing this in a terminal:
```
sudo updatedb
locate .B.blend 
```

(something like that anyway)

---

### Post by bluntu on 2006-08-17
Wow.... that's where it's been hiding.

/home/_username_/.B.blend

Now I'm curious, where does the 'updatedb' stores its info?

---

### Post by christhemonkey on 2006-08-18
Apparently:
> /var/lib/slocate/slocate.db

---

