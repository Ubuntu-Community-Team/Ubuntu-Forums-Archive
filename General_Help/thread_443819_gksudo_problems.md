---
title: "gksudo problems"
date: 2007-05-14
forum: General Help
---

### Post by jediborger on 2007-05-14
I am having a slight problem with gksudo and maybe someone knows a way around this. Basically does anyone know a way to have a command (gksudo for instance) run for a listing of stuff. Here's an example that might make more sense.
```
gksudo gedit --new-window
```
This gives me an error because gksudo doesn't have the --new-window option. I want the same output as
```
sudo gedit --new-window
```
but with the graphical pop-up for the root password. This might just be a basic linux syntax problem but I can't figure it out.

---

### Post by taurus on 2007-05-14
What kind of listing of stuff do you mean?  You do mean the listing the contain (files & directories) of a directory?

---

### Post by DoktorSeven on 2007-05-14
**gksudo "gedit --new-window"**

---

