---
title: "Setting properties in terminal mode"
date: 2005-08-03
forum: General Help
---

### Post by zoqaeski on 2005-08-03
I must be an idiot... I accidentally set the properties of a folder so that the owner could not read write or execute it, and now I can't unset them because I've locked myself out. ](*,)  :mad: 
So it seems the only way to change these is to modify the properties of the file in terminal mode, except I have no idea how to do that.

Whoops  ](*,) 

Does anyone here know? Like how to be able to manually set the bit that says "Text Mode: drwxr-xr-x" or whatever? Many thanks if you can help me...

Robbie

---

### Post by kvidell on 2005-08-03
Try this:
chmod 644 directory

---

### Post by Sam on 2005-08-03
```
$ chmod 755 <directory>
```
A directory should have the execute flag in order to open it.

---

### Post by zoqaeski on 2005-08-03
Can I please have a step-by-step explanation to this? It just comes back at me with 
bash: /home/robbie/files/lost-folder: is a directory

I really made a big mistake with this, didn't I?

---

### Post by Sam on 2005-08-03
Is your directory which causes you problems this one: /home/robbie/files/lost-folder ?
If so, open a terminal, (Applications, System Tools, Terminal), then type:
```
chmod 755 /home/robbie/files/lost-folder
```
Does this work ?

---

### Post by zoqaeski on 2005-08-04
Thanks! Fixed the problem!

---

