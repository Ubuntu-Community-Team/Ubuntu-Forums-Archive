---
title: "Gnome-Software doesn't load at all"
date: 2018-12-03
forum: General Help
---

### Post by amivaleo on 2018-12-03
Hi everybody,

Recently I've noticed that Software doesn't load anymore.
I use:
Ubuntu 18.04.1
Gnome Shell v. 3.28.3
Wayland session

If I try to run it from the terminal, I get nothing:
```
$ gnome-software
Timeout was reached
```

(I translated the output from my native language)
I get this timeout after a short time, like tens of seconds.

How can I get a verbose output from the terminal?
Do any of you have some idea on what to do to solve this?

I tried
```
$ rm -r ~/.local/share/gnome-software
```
```
$ sudo apt install -f --reinstall gnome-software
```
Still have the same issue...

---

### Post by TheFu on 2018-12-03
Let's verify that APT is ok first.

Run **sudo apt update**  Any warnings or errors?  If not, move on.  DO NOT go forward if there are any problems.

Next run** sudo apt upgrade**  Any warnings or errors?

Report back about those commands.

---

