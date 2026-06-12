---
title: "[SOLVED] When I open file explorer, it takes up the WHOLE screen. Help please"
date: 2008-02-16
forum: General Help
---

### Post by Lacent on 2008-02-16
Ok, so I have searched alot in the forums, and can't find anyone with a problem like this. When i open file explorer, it takes up the whole screen, including both my top and bottom bar. The only way I can exit it is by clicking file>exit, and I have to use alt+tab to change pages. Any help would be nice. See the screenshot also. Thanks

[IMG]http://i40.photobucket.com/albums/e235/psprockr/Screenshot.png[/IMG]

---

### Post by Anduu on 2008-02-16
Try launching it from a terminal using the --geometry command

```
nautilus --geometry 640x480
```

Resize it the way you like then close it.It *should* then relaunch that way.

---

### Post by Lacent on 2008-02-16
> **Anduu said:**
> Try launching it from a terminal using the --geometry command

```
nautilus --geometry 640x480
```

Resize it the way you like then close it.It *should* then relaunch that way.

That worked. Thanks alot!!! Will post as solved, if i can figure out how...

---

### Post by Anduu on 2008-02-16
Cool beans! :)

---

