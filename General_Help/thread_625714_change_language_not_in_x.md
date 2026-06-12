---
title: "change language? not in x"
date: 2007-11-28
forum: General Help
---

### Post by monkeyking on 2007-11-28
Hi, I need to change languages, but not in x.
In x, you can change the language using the command
```
setxkbmap us
```
Would change the keyboard layout to us english.

But If my system is in a runstate without X running.
how can i change the language then?

That is,
I'm not interested in something like

system->pref->keyboard->layout->??

But a command than will change the layout without the need for x running.


thanks in advance

---

### Post by qqzhenyi on 2007-11-28
this maybe helpful:
[http://www.linuxfromscratch.org/lfs/view/6.2/chapter07/console.html](http://www.linuxfromscratch.org/lfs/view/6.2/chapter07/console.html)

---

### Post by monkeyking on 2007-12-28
loadkeys us

will put the the console language into english.

for this to work
console-data might need to be installed

---

