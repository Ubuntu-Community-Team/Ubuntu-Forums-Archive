---
title: "Processes"
date: 2007-02-22
forum: General Help
---

### Post by Boule on 2007-02-22
Why is there so many processes running compared to windows ?

When I looked at the system monitor, and checked "My processes" in the view menu, I saw around 30 processes, which is pretty much the same than my window.

When I check all processes, the list is huge ! The install is fresh and I closed everything I was running. I see 6 instances of getty, what is that ? I also see one that says "gnome-cups-icon", and I don't have any printer installed !

---

### Post by john.nicholls on 2007-02-22
I have 92 processes running at the moment, which is somewhat fewer than usual. The six gettys are the terminals you can access from ctrl-alt-F1 to F6. If you run ```
ps aux
``` you will see that most of the processes are not actually doing anything.

---

### Post by Ramses de Norre on 2007-02-22
That's normal, it's just the way Linux works. Linux uses much more small processes where windows uses less but bigger processes.
I don't think there are any benefits from either of those methods, it's just a way of doing stuff.

---

