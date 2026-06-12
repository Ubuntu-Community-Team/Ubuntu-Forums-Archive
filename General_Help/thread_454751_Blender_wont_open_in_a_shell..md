---
title: "Blender wont open in a shell."
date: 2007-05-25
forum: General Help
---

### Post by tleave2000 on 2007-05-25
I have the latest version of blender in a folder in my home directory (it's great). But when I double click it, it doesn't open with the shell which is usually associated with it. I want the shell.  I tried right clicking on the program file and selecting properties - open with - and then entering /bin/bash, but that doesn't make any difference. Still no shell.

So, I tried placing this script on my desktop: 

```
#!/bin/bash

/home/tleave2000/Desktop/03_3d/blender_builds/blender-2.44-linux-glibc232-py24-i386/blender

```

That pretty much works, but it brings up a dialogue every time: "Do you want to run this script or display it?"
I almost always will want to run in a terminal so I'd like it to just automatically run in a terminal without asking me first. Is this possible? Incidentally when I do choose "Display", rather than "Run in a terminal" from the dialogue, it just opens the application without the shell as if I'd chosen "Run" instead. Any ideas why this might be?

Does anyone know a simple way to make blender (or any executable) open in a shell or how to fix the dialogue on my crummy (first ever) bash script?

Thanks for looking.

---

