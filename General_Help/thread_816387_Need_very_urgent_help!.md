---
title: "Need very urgent help!"
date: 2008-06-02
forum: General Help
---

### Post by GreigKM on 2008-06-02
My desktop is acting strange. When I log on the text is replaced totally with squares and nothing will run. I am running Ubuntu 8.04 x64. A screen shot of my desktop is included. Someone help!:(

---

### Post by Het Irv on 2008-06-02
What was the last thing you did before it started to do this?
Have you tried booting into (another Kernel / Recovory Mode)?
Can you open/use the terminal?

---

### Post by GreigKM on 2008-06-02
The last thing I did was install Cairo.
I have tried booting both the generic and rt kernel.
I can use the terminal (It's one of the few things that will open).

---

### Post by Tomatz on 2008-06-02
> **GreigKM said:**
> The last thing I did was install Cairo.
I have tried booting both the generic and rt kernel.
I can use the terminal (It's one of the few things that will open).

What language do you use in gnome (ubuntu)?

---

### Post by GreigKM on 2008-06-02
English, US.
This whole thing started from me attempting to install GTK+. In the process of meting it's requirements I guess something went wrong. (It needs GLib, Pango, and Cairo)

---

### Post by Het Irv on 2008-06-03
You can try removing and then reinstalling Cairo from the command line.

```
sudo apt-get remove cairo
sudo apt-get install cairo
```

---

### Post by GreigKM on 2008-06-03
Thank you! That did it! Then it was some kind of mishap during installation?

---

### Post by Het Irv on 2008-06-03
Thats what it sounds like.  Glad we could get it fixed, please mark your post as solved (thread tools, mark as solved).

---

