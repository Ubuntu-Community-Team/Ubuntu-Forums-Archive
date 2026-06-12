---
title: "blender will not run on my Ubuntu 12.04"
date: 2013-06-27
forum: General Help
---

### Post by oladitan on 2013-06-27
Hello I upgraded form ubuntu 11.10 to 12.04 and now blender 3D will no longer boot up properly. Here is my console output

```

oladitan@oladitan-ThinkPad-T42:~$ blender
 blender: swrast/s_span.c:1327: _swrast_write_rgba_span: Assertion `colorType == 0x1401 || colorType == 0x1406' failed. Aborted (core dumped)

```


Thank you.

---

### Post by DeathByDenim on 2013-06-27
It might be a bug in mesa. See here: [http://projects.blender.org/tracker/index.php?func=detail&aid=30944&group_id=9&atid=498](http://projects.blender.org/tracker/index.php?func=detail&aid=30944&group_id=9&atid=498)

Does Blender work if you start it like this?
```
LIBGL_ALWAYS_SOFTWARE=1 blender
```

---

