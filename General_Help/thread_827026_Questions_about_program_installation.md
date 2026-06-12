---
title: "Questions about program installation"
date: 2008-06-12
forum: General Help
---

### Post by oceanfirehawk on 2008-06-12
Hello everyone,

I have a question. First off, dont get me wrong...I like linux...i really do.


The question:  

Why, if linux is so advanced, am I required to use the command prompt to install simple programs like limewire, emulators, etc. I'm talking about programs that arent in the list of add/remove received from an online list. 

Why is the command prompt still used in linux so much. I am on a mac and I would switch to ubuntu forever if i didnt have to worry about the command prompt as much..

Thanks,
Jake

---

### Post by Titan8990 on 2008-06-12
Because it is faster and more powerful than those GUIs. Also, it takes a lot of work to create GUIs for everything and I don't believe that is on the top of the list for devs.

---

### Post by decoherence on 2008-06-12
Think of it this way: the software in the repositories is THE software for Ubuntu. If the software isn't in the repository, it isn't intended for Ubuntu.

**Because** Linux is such an advanced system (or more properly, 'open' as it's not significantly more advanced than other unix systems,) you can install programs that weren't intended for a specific distro. HOW you install such a program depends on the person who packaged the software as well as your own system. As such, it would be practically impossible to write a graphical install system that takes in to account all the variations in the software building process. That's why Ubuntu has a well defined package format and a program to manage them.

OS X is the same way. The only difference is that there is no central repository. But if you find an obscure enough program (or even one that isn't obscure but that nobody has written a .pkg installer for) you'll find you have to do the install on OS X in much the same way.

---

### Post by Pjotr123 on 2008-06-12
This is how you install software in Ubuntu the super easy way:
[http://ubuntutip.googlepages.com/installingapplications](http://ubuntutip.googlepages.com/installingapplications)

With Synaptic, you aren't limited to the apps in Add/remove.

---

### Post by wolfen69 on 2008-06-12
> **oceanfirehawk said:**
> 

Why is the command prompt still used in linux so much. I am on a mac and I would switch to ubuntu forever if i didnt have to worry about the command prompt as much..

Thanks,
Jake

just use Add/Remove if you prefer a GUI. or even Synaptic. or go to [www.getdeb.net](www.getdeb.net) to get packages. (single click install) but by the time you even open add/remove, i have typed: ```
sudo apt-get install application
``` and i am done. the command line is nothing to be afraid of. but there are gui only ways of doing things in ubuntu.

---

