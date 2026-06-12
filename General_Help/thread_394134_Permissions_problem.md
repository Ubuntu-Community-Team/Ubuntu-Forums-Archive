---
title: "Permissions problem"
date: 2007-03-26
forum: General Help
---

### Post by gannina on 2007-03-26
I am trying to run the following command on Ubuntu, but it keeps giving me a "Permission Denied" error.

```
sudo dpkg --get-selections > file-name
```

I just want to get a list of generated packages installed, and I'm the only one using this computer so I assumed I had access to everything.

---

### Post by aysiu on 2007-03-26
What directory are you trying to create *filename* in?

---

### Post by dannyboy79 on 2007-03-26
i didn't think this mattered if he is using sudo? also a quick way to list out all your installed packages is here: [http://www.ubuntuforums.org/showthread.php?t=209064](http://www.ubuntuforums.org/showthread.php?t=209064)

---

### Post by stchman on 2007-03-26
> **aysiu said:**
> What directory are you trying to create *filename* in?

Should it matter since he is running sudo?  I thought sudo is root and root has all the permissions.

---

### Post by aysiu on 2007-03-26
I've run into some problems with *sudo* carrying over after *>>* to the second part of the command. Not sure if it applied to *>* as well.

---

### Post by ardchoille42 on 2007-03-26
sudo can fail to carry over redirections and pipes. Perhaps this would be better:

```

sudo dkpg --get-selections > ~/file-name

```

---

### Post by gannina on 2007-03-28
When I rebooted and tried the command it worked no problem. I think I might of typed the wrong password for sudo too many times :( Is restarting the only way to fix this?

---

