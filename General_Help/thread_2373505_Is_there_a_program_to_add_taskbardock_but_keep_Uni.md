---
title: "Is there a program to add taskbar/dock but keep Unity???"
date: 2017-10-06
forum: General Help
---

### Post by pretty_whistle on 2017-10-06
I have Ubuntu 16.04.2 64 bit with Unity.  

I'd like to know if there's a program where I can add a taskbar or dock but not rid Unity like Cairo Dock would do.  I'd like to have both if that's possible.  Know of any good program for this??

Thanks for help.  :KS

---

### Post by again? on 2017-10-06
Why can't you run cairo-dock in unity?

---

### Post by pretty_whistle on 2017-10-06
According to what I read it would replace Unity unless I misunderstood it.

---

### Post by again? on 2017-10-06
No ...just runs like in any other desktop environment.
When you install cairo-dock it also adds a cairo-dock session without unity that you can use if you wish
but you can also just autostart cairo-dock in the Ubuntu session.
If you want something more lightweight than cairo-dock, install plank.

---

### Post by pretty_whistle on 2017-10-06
If I could do both at once I'd take it.  :/  I mean, I'd like to use Unity but have another dock running inside Unity (making myself more clear).

---

### Post by again? on 2017-10-06
> **pretty_whistle said:**
> If I could do both at once I'd take it.  :/  I mean, I'd like to use Unity but have another dock running inside Unity (making myself more clear).
Edited my previous post for clarity.

---

### Post by pretty_whistle on 2017-10-06
Autostart cairo dock?  I wonder how to do that using the terminal.......

---

### Post by again? on 2017-10-06
Why use terminal?
What's wrong with startup applications?
> **_With OpenGL _**
In the command field, execute Cairo-dock as follows 
cairo-dock -o

**_Without OpenGL / With the Cairo backend _**
If you've experienced any trouble with OpenGL, use the Cairo backend 
In the command field, execute Cairo-dock as follows 
cairo-dock -c


---

### Post by pretty_whistle on 2017-10-06
Ok, installed it and its working out great.  Just what I wanted.  I didn't know I could run it inside Unity and have both!

I'll mark this as solved.

---

