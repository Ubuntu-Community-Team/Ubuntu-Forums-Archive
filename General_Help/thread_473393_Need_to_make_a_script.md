---
title: "Need to make a script"
date: 2007-06-14
forum: General Help
---

### Post by herbster on 2007-06-14
I want to make a script that stops conky when I play ET and then starts it again when I quit the game. To run the game I use:

```

./etsound

```

TIA for any help!!

---

### Post by girishv on 2007-06-14
Cant you use a simple one line command
pkill conky && etsound && conky

Unfortunately it will work only if conky is already running as the second command succeeds if 
the first command (killing conky) returns true.

You can alias this to something so that you dont have to type it everytime

Girish

---

### Post by herbster on 2007-06-14
Girish,

Thanks! I just tested it, changed to "./etsound" and it works perfectly.

How do I "alias" it? I'm assuming you mean making it a simple file I can run instead of typing it each time, that would be great!

---

### Post by herbster on 2007-06-14
So I have my conky now working as dual-conky which runs both my conkyrc's. I do this in shell:

```

pkill conky && ./etsound && dual-conky
```

and it works just fine, but if I change my shortcut on my gnome panel's command to the above, it doesn't do anything.

If someone can help me put that above into a one-click script or something that would be great!

---

