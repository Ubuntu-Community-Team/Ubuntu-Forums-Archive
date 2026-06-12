---
title: "Problems with adding to rc.local"
date: 2008-02-05
forum: General Help
---

### Post by lonnieh on 2008-02-05
I'm working on a MAME cabinet and my setup includes a trackball with an old serial interface. 
Is there a way to have both USB and serial mice attached to the system? I've tried to add some lines to xorg.conf, but I can't get both working, just one or the other. 
I can enable the trackball with 'inputattach -ms /dev/ttyS0' and I've added that line to rc.local and set the execute bit. Now when I attempt to restart or shutdown the system goes into 'single user mode', I'm not quite sure what to do to get the script to exit correctly (sounds like that may have something to do with it?)

---

### Post by pointone on 2008-02-05
Simply make sure the last line in rc.local is "exit 0".

Also make sure "inputattach -ms /dev/ttyS0" isn't failing. $? returns the exit status of the last executed command.

```
inputattach -ms /dev/ttyS0
echo $?
```

---

