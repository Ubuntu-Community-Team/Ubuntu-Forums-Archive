---
title: "Do I need &quot;echo $PACKAGE hold&quot;?"
date: 2014-06-04
forum: General Help
---

### Post by Mk32 on 2014-06-04
Hi, 

I am compiling some software from source. Specifically, Netatalk. Also, I'll probably have to compile Engima from source.

Do I need this line after I have run the sudo make and sudo make install commands? 

```
echo "netatalk hold" | sudo dpkg --set-selections
```

As far as I know, this tells dpkg to ignore netatalk when it checks the system for updates. This is ideal because I'm running an older version of Netatalk and upgrading it would break the purpose (geek details: Netatalk 2.x has EtherTalk support, Netatalk 3.0 does not. I need EtherTalk).

---

### Post by Mk32 on 2014-06-07
I take it then, it's optional...

---

### Post by Mk32 on 2014-06-10
Well, I'll post what I've found, and what I believe is correct. 

Compiled from source programs don't need the line: only ones that are installed via something like APT, using [FONT=courier new]sudo apt-get install <filename>[/FONT] in this case. So if you were installing an older version of gedit for instance from a repository, then yes you would need it so the next time the Update Manager rolled around it would ignore it for updating.

---

