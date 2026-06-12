---
title: "Finding .bash_profile file"
date: 2007-08-18
forum: General Help
---

### Post by ryuninja on 2007-08-18
Ive searched all over and cant find the .bash_profile file.  Ive tried the ls -a command and all I see is .bash_logout  .bash_history  .bashrc.   I need to find the .bash_proflie file so that I can edit it to load my script paths automatically.  I'm running the latest desktop version of Ubuntu.  I would greatly appreciate any help, thanks in advance.

---

### Post by colo on 2007-08-18
Just create the file, and make it executeable.

```
touch ~/.bash_profile
chmod 700 ~/.bash_profile
```

---

### Post by ryuninja on 2007-08-18
Ok, I created the file and set the permission rules with your code but  since I'm very much a noob at all this I don't quite know how to make it "executable". I guess I sorta need a small walk through on how to set the file up.

---

### Post by kerry_s on 2007-08-18
> **ryuninja said:**
> Ok, I created the file and set the permission rules with your code but  since I'm very much a noob at all this I don't quite know how to make it "executable". I guess I sorta need a small walk through on how to set the file up.

chmod +x ~/.bash_profile

---

