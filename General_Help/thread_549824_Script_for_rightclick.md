---
title: "Script for rightclick"
date: 2007-09-13
forum: General Help
---

### Post by Visti on 2007-09-13
Hi! I was wondering if I can somehow write a script or something so that when I rightclick an iso-file I can get an option to mount it. It seems straight-forward, since the mount command is almost always the same, but I don't know where to edit or how to do it. How would I go about doing this?

Greetings,
Visti

---

### Post by Jussi Kukkonen on 2007-09-13
> **Visti said:**
> Hi! I was wondering if I can somehow write a script or something so that when I rightclick an iso-file I can get an option to mount it. It seems straight-forward, since the mount command is almost always the same, but I don't know where to edit or how to do it. How would I go about doing this?

Greetings,
Visti

Assuming you're using nautilus, you should write a nautilus script:
[http://g-scripts.sourceforge.net/](http://g-scripts.sourceforge.net/) (see the FAQ)

Should be fairly easy, something like```

#!/bin/sh
your_mount_command "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS"
```
should do it. This will only work for single files, but I can't see why you'd want to mount several ISOs at a time anyway.

---

### Post by capink on 2007-09-13
I don't use nautilus, but I think it is possible using nautilus scripts. If you  use thunar, [here]("http://ubuntuforums.org/showpost.php?p=3256387&postcount=5") is a way to do it.

---

