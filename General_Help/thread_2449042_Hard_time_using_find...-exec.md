---
title: "Hard time using find...-exec"
date: 2020-08-18
forum: General Help
---

### Post by raleigh3 on 2020-08-18
I am having a hard time understanding how to use -exec.

I am trying to delete all .deb files.

This does not work and returns no messages when run.

```
find /home/andy/.local/share/Trash/expunged/ -type f -exec rm {*.deb} \;
```

---

### Post by GhX6GZMB on 2020-08-18
Why are you searching for files in the garbage can?

You'll need to rearrange the command, I think.

---

### Post by raleigh3 on 2020-08-18
The files themselves go to 

```
/home/andy/.local/share/Trash/files/
```

My entire script.
```

#!/bin/bash
find /home/andy/.local/share/Trash/expunged/ -type f -exec rm {} \;
find /home/andy/.local/share/Trash/files/ -type f -exec rm {} \;
find /home/andy/.local/share/Trash/info/ -type f -exec rm {} \;
```

The script works with all deleted files except .deb files?

---

### Post by raleigh3 on 2020-08-19
```
rm /home/andy/.local/share/Trash/files/*.deb
```

---

### Post by kneutron on 2020-08-19
--Try this (not tested)

[COLOR=#000000][INDENT]find /home/andy/.local/share/Trash/expunged/ -type f -name *.deb -exec /bin/rm -fv {} \;
[/INDENT]
[/COLOR]

---

