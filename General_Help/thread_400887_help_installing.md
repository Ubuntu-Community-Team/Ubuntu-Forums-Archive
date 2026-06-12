---
title: "help: installing"
date: 2007-04-04
forum: General Help
---

### Post by Donhu on 2007-04-04
i got an error while installing beryl...it says : " "libGL warning: 3D driver claims to not support visual 0x5b
Reloading options" "
have no idea wat i did wrong...help

---

### Post by amohanty on 2007-04-04
Some questions:
1. what kind of video card do you have?
2. What driver are you using?
3. Did you install xgl
4. What beryl install guide are you using?

AM

---

### Post by Donhu on 2007-04-04
i got a  i915 intel driver, wat's xgl?
im jus going by the steps under the intel section

---

### Post by amohanty on 2007-04-04
Whoops assumed too much. 
Can you post the output of 

glxinfo | grep direct

AM

---

### Post by Donhu on 2007-04-04
yea i think you did...and still are...lol how do i get to those places i.e. glxinfo | grep direct

---

### Post by amohanty on 2007-04-04
Oh! sorry :)
1. Bring up a terminal:
Applications->Accesories->Terminal
2. Type in:
**glxinfo | grep direct**

The first command provides info about the opengl acceleration provided by your driver, which is then ***piped*** into the command **grep** which stands for (i think) gnu regular expression parser, which is a fancy text search tool that searches for the text **direct** in the text thats produced by **glxinfo**

Select the output. MIddle click in the reply box.

HTH
AM

---

### Post by Donhu on 2007-04-04
ok did that...i got this as the output...

libGL warning: 3D driver claims to not support visual 0x5b
direct rendering: Yes

---

### Post by Maestro23 on 2007-04-04
Take a look at the 915resolution package as well.

If you have all your repositories added, you should be able to get it.
Adding Repositories: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

> sudo aptitude install 915resolution

Can also look it up via Synaptic and it will give a description of what it is.

Good luck.

---

### Post by amohanty on 2007-04-04
Hmm...
Take a look in the beryl forums and see if any suggestions help:

[http://forum.beryl-project.org/search.php?keywords=libGL+warning+support+visual+0x5b&terms=all&author=&sc=1&sf=all&sk=t&sd=d&sr=posts&st=0&ch=200&sid=179891255799f2dd0915d8f1da3e0be2&t=0&submit=Search](http://forum.beryl-project.org/search.php?keywords=libGL+warning+support+visual+0x5b&terms=all&author=&sc=1&sf=all&sk=t&sd=d&sr=posts&st=0&ch=200&sid=179891255799f2dd0915d8f1da3e0be2&t=0&submit=Search)

AM

---

### Post by Donhu on 2007-04-04
ok man thanks alot

---

