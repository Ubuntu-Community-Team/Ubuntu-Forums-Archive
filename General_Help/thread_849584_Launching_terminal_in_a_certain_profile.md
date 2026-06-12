---
title: "Launching terminal in a certain profile?"
date: 2008-07-04
forum: General Help
---

### Post by LightningEagle on 2008-07-04
I don't know if this is asked before or perhaps I'm putting this in a wrong category, but I did a search and didn't find anything so now I'm asking: 

Is it possible to make a launcher which launches the standard terminal found under: Applications -> Accessories -> Terminal | - in another profile than default? 

And in case it is: how do I do it?

---

### Post by Vivaldi Gloria on 2008-07-04
> **LightningEagle said:**
> I don't know if this is asked before or perhaps I'm putting this in a wrong category, but I did a search and didn't find anything so now I'm asking: 

Is it possible to make a launcher which launches the standard terminal found under: Applications -> Accessories -> Terminal | - in another profile than default? 

And in case it is: how do I do it?

Try

```
gnome-terminal --window-with-profile=PROFILENAME
```

See 

```
man gnome-terminal
```

---

### Post by LightningEagle on 2008-07-04
Yay, it's working exactly as I hoped! :D

Thank you.

---

