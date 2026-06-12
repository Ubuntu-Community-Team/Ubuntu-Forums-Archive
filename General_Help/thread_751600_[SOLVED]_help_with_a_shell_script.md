---
title: "[SOLVED] help with a shell script"
date: 2008-04-10
forum: General Help
---

### Post by Tyke91 on 2008-04-10
Blender will not start properly in a composting window manager, but it will run fine in one once started. So I'm trying to put together a shell script to automate this for me.

the script looks like this
```

#!/bin/sh
metacity --replace 

blender --windowed

compiz --replace

```the only problem is that the script won't move on to the next command until the previous is finished, and the command metacity --replace doesn't finish until you close the terminal in which you gave it. But once you close that terminal, you close the terminal that the rest of the code is supposed to run in as well... which kills the entire script.


does anyone have any advice about how to get around this?

---

### Post by dje on 2008-04-10
just try this:
```
#!/bin/sh
metacity --replace &

blender --windowed

compiz --replace
```

hope that helps,
dje

---

### Post by Tyke91 on 2008-04-10
thanks, you didn't solve it, but you helped me solve it.
```

#!/bin/sh
metacity --replace &

blender --windowed &

compiz --replace

```gave the desired effect

Marking as solved - also, could somebody tell me how to change the name of a forum thread? :) I know that mods can do it, so if I can't do it as a normal user, could a mod please rename this thread as "Starting Blender in Compiz"

---

### Post by dje on 2008-04-10
Ah, glad you sorted it. I thought you meant compiz was causing a problem throughout running blender

dje

---

### Post by bodhi.zazen on 2008-04-10
& = run in background

I suggest you put an & at the end of compiz --replace as well ;

```
#!/bin/sh
metacity --replace &

blender --windowed &

compiz --replace &
```

---

### Post by Tyke91 on 2008-04-10
thanks for the tip

EDIT: the & at the end of compiz --replace will do something wierd. It gives the same effect as running blender directly from compiz, it gives no window... 
still, thanks for the tip, i never knew what the & did before.

---

