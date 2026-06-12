---
title: "C on ubuntu?"
date: 2006-10-17
forum: General Help
---

### Post by Dimitar on 2006-10-17
Hey everyone,
i was wondering if someone could help me out.

Ive just installed ubuntu, and it seems that it doesnt come with gcc, can someone tell me where to get it? also how to reference to my libraries. 

Another question is, at uni, were running Fedora, core 5 i think... not really sure, anyway, if i were to use the .cshrc on my ubuntu machine would i be able to use all the settings in there? or would it crash my machine?

Any help would be much apprieciated.

Thanks,
Dimitar

---

### Post by hod139 on 2006-10-17
To get gcc (along with everything else required for programming) install the package build-essential.

---

### Post by mssever on 2006-10-18
> **Dimitar said:**
> Another question is, at uni, were running Fedora, core 5 i think... not really sure, anyway, if i were to use the .cshrc on my ubuntu machine would i be able to use all the settings in there? or would it crash my machine?

You can use your .cshrc without fear of crashing your machine (it's impossible, barring bugs, for a file in your home directory to crash the machine). However, you need to be using the C shell in order for your .cshrc to have any effect. Ubuntu's default shell is bash; if you want to use csh, do ```
sudo apt-get install csh
```

To temporarily change to csh, type csh. To make csh the default shell, type ```
chsh /bin/csh #assuming this is the proper path--I don't actually use csh
```While I've always used bash, I always copy my .bashrc to every system I use and I haven't had any difficulties.

---

### Post by Dimitar on 2006-10-18
big thanks. all works well.

---

