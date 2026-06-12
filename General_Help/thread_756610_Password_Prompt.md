---
title: "Password Prompt"
date: 2008-04-16
forum: General Help
---

### Post by MNICY on 2008-04-16
Ok, so you know how in Ubuntu when you run a program that can change parts of your system from the program menu, and it brings up prompt pops up asking for the password?
well, i was wondering if there was some sort of command that i could run to get a program to do that.

If I run a command in terminal, such as "sudo nautilus", it asks for my password in the terminal window, then opens up nautilus (with root permissions).

If i want to make a launcher to launch nautilus with root permissions, how would i do that? If i put "sudo nautilus", then it does not work. If i run in terminal, it works, but it is not very nice.
Which is why i ask, is there a way to get that pop up which asks for the password?

---

### Post by sekinto on 2008-04-16
You shouldn't be using sudo for graphical applications, only for CLI apps. "gksudo" would be better.

From terminal:
gksudo nautilus

Launcher command:
gksudo nautilus

---

