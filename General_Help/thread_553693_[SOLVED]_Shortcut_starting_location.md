---
title: "[SOLVED] Shortcut starting location"
date: 2007-09-18
forum: General Help
---

### Post by Kenchu on 2007-09-18
Im having trouble creating a shortcut to a WinXp app. Thing is, i have to "be" in the same directory as the windows app for wine to work. Using "wine path/to/app" doesnt work. Need to "cd" my way there and then run "wine app.exe". How can I make a shortcut out of that? Can i say where (folder) the shortcut should start?

---

### Post by Jussi Kukkonen on 2007-09-18
One solution. Create a script like this:
```

#!/bin/sh

cd /full/path/to/app/
wine app.exe

```
Save the script  somewhere (I have mine in *~/bin/*), and make it executable (*chmod +x  ~/bin/script_file*). Then have your launcher run the script.

---

### Post by Kenchu on 2007-09-18
Thx. Works like a charm.

Btw. Something that has been bugging me for a while now. What does that "!" mean in #!/bin/sh? And how can I add ~/bin/ to path-variable?

---

### Post by Jussi Kukkonen on 2007-09-19
"#!" as a whole is the "shebang". It informs the shell that the rest of the line is the name of the interpreter that should be used to run this file (bash, python, awk, whatever). As a matter of fact "#!" is just the ascii representation of the actual bytes that form the shebang -- chosen probably because the ascii version looks like a comment in many scripting languages.

---

