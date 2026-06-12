---
title: "get custom app to show up in search?"
date: 2019-03-14
forum: General Help
---

### Post by tburns3 on 2019-03-14
I copied an app from one ubuntu PC to another. Now I can invoke it from the command line, but it doesn't show up in the search thing. How do I get it to show up in the search thing along with the other apps?

Sorry, I'm not sure which forum to ask this question or how to word it even. If this is the wrong place, please point me in the right direction, I am clueless.

---

### Post by DuckHook on 2019-03-14
We really do sympathize with the fact that a new operating system is obscure and overwhelming, but it is difficult to help without complete info or precise language.

[LIST=1]
[*]What app? Why can't you give us its name?
[*]Why copy it across PCs? That's not how apps are installed in the Ubuntu ecosystem. Each device should be downloading it from the Ubuntu repositories.
[*]How are you invoking it from the command line?
[*]What is the "search thing"? There are many ways to search in Ubuntu, along with many containers in which apps and launchers can reside. Without a better description, we have no idea what you are referring to. If you don't know the name of the desktop element you are referring to, describe in detail what you do to get to it.
[/LIST]

---

### Post by Dennis N on 2019-03-14
> How do I get it to show up in the search thing along with the other apps?
If you make a .desktop file for the program and put it in ~/.local/share/applications, it will be found when you search from Ubuntu's activities overview screen.

---

### Post by tburns3 on 2019-03-15
Thanks Dennis N, that was the hint I needed.

---

