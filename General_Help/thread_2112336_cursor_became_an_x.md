---
title: "cursor became an x"
date: 2013-02-04
forum: General Help
---

### Post by thorbs on 2013-02-04
All of sudden the cursor became an x. And the windows and panels is not working optimal. 

help?

---

### Post by Impavidus on 2013-02-04
Sounds like the default X (as in X windowing system) pointer that I haven't seen in years. Maybe your standard pointers have gone somehow and your system is using a fallback. Are you using the default desktop environment of 12.04 or 12.10?

---

### Post by thorbs on 2013-02-04
I am not sure what I am using.

Until just two hours ago I was using the standard zubuntu 12.10 enviroment. I dont know what happened or why it has fallen back.

t.

---

### Post by Impavidus on 2013-02-04
Zubuntu? I assume you meant to type Xubuntu. Xubuntu sometimes has a problem with the interface. Typing the command```
xfwm4 --replace
``` often works.

---

### Post by thorbs on 2013-02-04
It works but only for one session. Next time I turn the computer back on, I am having the same problem, but the same solution also works again.

t.

---

### Post by thorbs on 2013-02-05
I dont know if it was clear what I tried to explain.

When I use the command xfwm4 --replace it works. But only for the session. When I restart the computer the same problem is there.

Is there anybody who knows a permanent fix?

---

### Post by Impavidus on 2013-02-06
I've never seen this problem being so consistent. If you wish, you could try to put the command in the list of default applications at login. Maybe you have to put a delay in front.

---

### Post by thorbs on 2013-02-06
I was thinking the same but it seems like a less than optimal choice.

---

### Post by thorbs on 2013-02-12
Nobody who have a permanent soution for this?

---

### Post by thorbs on 2013-02-19
Ok, the problem disapeered by itself on the next automatic upgrade of the Kernel.

---

