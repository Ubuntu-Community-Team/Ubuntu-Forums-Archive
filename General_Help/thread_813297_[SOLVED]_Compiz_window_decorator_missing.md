---
title: "[SOLVED] Compiz window decorator missing"
date: 2008-05-30
forum: General Help
---

### Post by solidus126 on 2008-05-30
Hello!

Since the latest package updates, Compiz has stopped decorating my windows after logging in. I am left without a title-bar, and minimize/maximize/close buttons.  The window decorations only come back if I use compiz --replace or an option in the program fusion-icon to reload it.  I am using Kubuntu with rock solid KDE.

Any ideas?  Thanks!

-solidus126

---

### Post by solidus126 on 2008-05-30
bump

---

### Post by prshah on 2008-05-31
> **solidus126 said:**
> 
Since the latest package updates, Compiz has stopped decorating my windows after logging in. 

Have you tried adding the compiz --replace command to your startup sessions? Just a suggestion...

---

### Post by solidus126 on 2008-05-31
I have very little startup scripting experience, would a bash script with that one line be good enough?

---

### Post by solidus126 on 2008-05-31
OK, I am going to say this is resolved, here is a script that I wrote and put in my Autostart folder:

```
#!/bin/bash
kde-window-decorator --replace
```

You may want to put:
compiz --replace

as the second line as a last resort if the decorator still does not run. I saw a significant (5-10 second) delay by having that line in there, and after experimentation found that just that one line seemed to be all I needed.

Thanks for the suggestion!

-solidus126

---

