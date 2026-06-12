---
title: "makeing a quick launch menu item from a shell script"
date: 2007-08-02
forum: General Help
---

### Post by Luksion Knight on 2007-08-02
hey i have sauerbraten configured, and running when i execue it, but i want to make a launch button in my games menu. but it wont work. ive tried different commands, ive made it application, and application in terminal. but it will not work. the closest i get is "There was an error creating the child process for this terminal" can someone help?

---

### Post by nichipet on 2007-08-02
What did you do which gave you "There was an error creating..." ? If we know what came close, it can make finding the solution easier.

---

### Post by Luksion Knight on 2007-08-02
i dont know if it even came close, it was just the only thing that didnt make the terminal come up then close. it was ./loacation/of/program/sauerbraten_unix

---

### Post by nichipet on 2007-08-02
Try this, it's not a great solution, a bit quick and dirty, but it will hopefully work.

In Terminal:

```
gkedit runsauerbraten.sh
```

Or use any other text editor, vim, emacs, etc.

Once in the file:

```
cd /path/to/sauerbraten
./sauerbraten_unix
```

Back in terminal:

```
chmod +x runsauerbraten.sh
```

Then try adding runsauerbraten.sh to your desktop, and see if it works from there. If it does, the rest can be achieved.

---

### Post by Luksion Knight on 2007-08-02
thanks a ton, its working perfectly!

---

