---
title: "i think i broke my pictures folder with chmod -R..."
date: 2006-07-04
forum: General Help
---

### Post by oldmanstan on 2006-07-04
so, i've done a chmod -R before to protect files against accidental overwrite, however this time i decided that in order to prevent myself from opening a picture and accidentally hitting "save" instead of "save as" after playing with it i would chmod -R 440 the whole pictures directory... (kinda ironic)

well it errored out

```
george@stan:~$ chmod -vR 440 Pictures
mode of `Pictures' changed to 0440 (r--r-----)
chmod: `Pictures': Permission denied
failed to change mode of `Pictures' to 0440 (r--r-----)
```

and now my pictures directory has 130 objects totalling 0 bytes, all the subdirectories appear as random files (which can't be accessed) in nautilus and the files are empty... did i blow it? or can it be fixed? any ideas? thanks

---

### Post by deeek on 2006-07-04
No, you didn't blow it.  What happened was that when you changed the permission for your "Pictures" directory, you set it to read only and now you can't cd into that directory.  You should have changed it to 550 instead of 440. 

To fix this, in a terminal, you must 
```

sudo chmod -vR 550 Pictures

```
and then all should be fine.

EDIT:  Well, I thought that should have worked, but it doesn't seem to.  Hmmm...

---

### Post by halfvolle melk on 2006-07-04
Well, I don't know but I'd throw a "sudo chown -R george Pictures" at it. What's the point of pictures if you can't look at them! And then you can take it from there.

nevermind: see above.

---

### Post by oldmanstan on 2006-07-04
thank you greatly, both of you!

i was really worried, i didn't realize you had to have exec. priv. to cd into a directory, now i know :)

i love learning more about this shell stuff, reminds me of when i was a kid, haha

---

