---
title: "Software Centre won't start"
date: 2016-11-17
forum: General Help
---

### Post by Skunky-One on 2016-11-17
I'm having a weird problem with 16.10. If I click on Ubuntu Software, nothing happens. The wheel spins around for a while, then that's it. Most recently, 16.10 performed system updates. I had tried to install Arduino, but I wasn't able to. Ubuntu Software asked me for my password. I used the correct one - the same one I used to login to this forum, but Ubuntu Software wouldn't accept it. I restarted, and now Ubuntu Software won't open.

Strangely, Ubuntu Software has never asked for the system (root) password when I'm installing or removing packages.

---

### Post by cariboo on 2016-11-19
Moved to a thread of it's own.

---

### Post by Bucky Ball on 2016-11-19
Welcome. Can you install things from the terminal? Try installing another package manager and see if that works. Doesn't fix the original problem but gives you a package manager and has worked for others.

```
sudo apt install synaptic
```

Let us know if that throws the same error.

>  Strangely, Ubuntu Software has never asked for the system (root) password when I'm installing or removing packages. 

It is strange because it should. :-k Are you logged in as root? Definitely not advisable unless you have a very good reason to do so, and can't think of many.

---

