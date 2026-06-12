---
title: "Creating self-executing scripts"
date: 2007-06-02
forum: General Help
---

### Post by kylor on 2007-06-02
I created a simple script to launch a certain game:

```
cd /usr/games/regnum
./rolauncher
```

Don't ask why the script is necessary. The question is, how do I get this file to automatically execute itself from a double-click? If I check "allow executing file as a program", it still gives me a little dialog asking me whether to open it or run it. What I want it to do is run itself without this dialog.

I tried making it open with the command "sh", but then all the text files on my computer start running with that command, even though I named the file with ".sh" at the end and it says it's a shellscript file.

Can anyone help, or is there nothing I can do about it?

---

### Post by yabbadabbadont on 2007-06-02
Try changing ```
cd /usr/games/regnum
./rolauncher
``` to ```
#!/bin/bash
cd /usr/games/regnum
./rolauncher
``` then make the file executable ```
chmod 755 scriptfilename
```

---

### Post by Azakus on 2007-06-02
Another way to do it is
```
chmod +x script
```

---

