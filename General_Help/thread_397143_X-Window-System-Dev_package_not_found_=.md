---
title: "X-Window-System-Dev package not found =\"
date: 2007-03-30
forum: General Help
---

### Post by Bahbuu on 2007-03-30
Hey

I'm trying to install x-window-system-dev

but when I type

"sudo apt-get install w-window-system-dev" 

I get an error:

E: Couldn't find package x-window-system-dev


Where can I get it ??? 


Thanks!

---

### Post by Bahbuu on 2007-03-30
oh nevermind,
I found it

but it requires pm-dev

found that also

but then it requires xfree86-common
which conflicts will x11-common [already present on my machine]

but when I tried removing x11-common
[[sudo apt-get remove x11-common]]

I get an error that i can't remove it

are there any other ways to install x-window-system-dev?
[I need it to install some programs]

---

