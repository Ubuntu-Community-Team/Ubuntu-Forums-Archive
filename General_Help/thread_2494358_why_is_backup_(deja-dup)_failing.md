---
title: "why is backup (deja-dup) failing?"
date: 2024-01-14
forum: General Help
---

### Post by Acharn on 2024-01-14
It seems like every week backup reports that it failed. When I open the GUI, it says something like, "last backup 10 days ago." Why is deja-dup telling me that it failed? Is there something I need to change? How can I find out what it is?

---

### Post by TheFu on 2024-01-14
I don't use deja-dup, but the normal method to find and fix issues is to review the log files. Have you done that?

A second method is to run the program directly from a terminal and watch (capture) the output for issues.  Sometimes this is the easiest, provided the GUI library doesn't dump thousands and thousands of unrelated crap.

---

### Post by Acharn on 2024-01-15
Sounds like a good idea. Where/how do I find the log files for deja-dup?

---

### Post by TheFu on 2024-01-15
> **Acharn said:**
> Sounds like a good idea. Where/how do I find the log files for deja-dup?

That's an excellent question.
How might you find the answer, without asking here?

As I said, 
>  I don't use deja-dup, but the normal method to find and fix issues is to review the log files. Have you done that?

You already have the fishing pole. Are you really asking someone else to get their fishing pole out, drop the lure, catch the fish, then hand the fish over to you for something this easy?
[https://welcome.gnome.org/app/DejaDup/](https://welcome.gnome.org/app/DejaDup/)

---

### Post by deadflowr on 2024-01-15
As far as I know there is no logging, by default.
You can run in debug mode which will output what's going on.
In the terminal
```
DEJA_DUP_DEBUG=1 deja-dup --backup
```
I don't think it produces a file so you might need to run a redirect of whatever the output is to one if you want to keep it outside of the terminal output.
It is a debugging mode so it'll probably output a large amount of data, more so than a regular run would. Buyer beware, I guess.

---

