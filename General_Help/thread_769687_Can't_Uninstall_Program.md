---
title: "Can't Uninstall Program"
date: 2008-04-26
forum: General Help
---

### Post by DocHolliday2006 on 2008-04-26
Hi. I installed an emulator called Gens right before downloading Hardy Heron. I never got a chance to open it, but now with Heron installed, I noticed that it won't open. It just crashes immediately.

 I need to uninstall it, but I installed it from a downloaded package, not from the add remove programs menu. There is no listing for it on add/remove programs, so how do I open it?

---

### Post by catalina on 2008-04-26
Hi Doc,

You have to navigate using the terminal to the directory that the files are located in.  You can use "sudo rm <filename>" once you have used "cd" to change to the directory/files you want to remove.  Just remember...you have to use "sudo rmdir" to remove a directory and "sudo rm" to remove files.

Something you can try is "sudo apt-get autoremove" and see if it is considered an orphaned package.  If it is it will remove it, if not, try the steps above.

Not an expert but hope it works!

---

### Post by scragar on 2008-04-26
if you still have the .deb installer then it's fairly easy:
```
dpkg -P **PATH/TO/PACKAGE**
```
if you don't have the package then I'm not sure, since you would need a list of what's been installed for it to be safely removed.

---

### Post by ibuclaw on 2008-04-26
What was the suffix of the package that you installed it with?

Also, where did you download it from?

It may be locatable.
We'll aid you in minimising the effort and strain on you :)

Regards
Iain

---

### Post by joshsmith on 2008-04-26
open up synaptic, and see if the package is listed there, and remove it.

it should be there if you installed it from a deb, if not, could you tell us how you installed this program?

---

### Post by scragar on 2008-04-26
1 quick question, have you tried different things? Like opening it from a terminal to see what error messages it gives, or opening a rom using it? Maybe it's not crashing, but just needs some form of special treatment.

---

### Post by DocHolliday2006 on 2008-04-26
> **joshsmith said:**
> open up synaptic, and see if the package is listed there, and remove it.

it should be there if you installed it from a deb, if not, could you tell us how you installed this program?


I found it by loading synaptic, but it was not in add/remove programs. Thanks very much for the suggestion.

---

### Post by scragar on 2008-04-26
there is no program by the name of gens to be found on any ubuntu package listings...

are you sure it was called gens, did you have to add a repository first, and if so which? Are you sure it was installed using synaptic?

---

### Post by DocHolliday2006 on 2008-04-26
> **scragar said:**
> there is no program by the name of gens to be found on any ubuntu package listings...

are you sure it was called gens, did you have to add a repository first, and if so which? Are you sure it was installed using synaptic?

Not sure if I explained. It was in synaptic, so I uninstalled it. It was not in add/remove.

The problem is fixed. Thanks very much.

---

