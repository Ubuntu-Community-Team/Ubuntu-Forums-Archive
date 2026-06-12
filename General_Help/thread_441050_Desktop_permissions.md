---
title: "Desktop permissions"
date: 2007-05-12
forum: General Help
---

### Post by mhenriday on 2007-05-12
I've managed, entirely inadvertently, to arrange my desktop in such a way that I can no longer download files to it, move them there from my home directory, or remove files from it. When I try, I am informed that I don't have the necessary permissions to perform these operations. Previously, I had no such difficulties, and I should have thought that no such problems would exist for me as Administrator. What did I do wrong and how do I regain access to my desktop ?...

Henri

---

### Post by Theimon on 2007-05-12
```
sudo chown -R "yourusername:yourusername" /home/"yourusername"
``` Without quotes ofcourse.

---

### Post by heimo on 2007-05-12
I'd try:
[HTML]sudo chown $USER:$USER ~/Desktop
chmod 755 ~/Desktop
[/HTML]

---

### Post by mhenriday on 2007-05-12
> **heimo said:**
> I'd try:
[HTML]sudo chown $USER:$USER ~/Desktop
chmod 755 ~/Desktop
[/HTML]

*Paljon kiitoksia*, **heimo** ! I did try it, and it worked like a charm, as I realised it would immediately after seeing the 755. Chalk my query up to my lack of 'Nix experience ; otherwise I'd have been able to deduce the proper command. But I wonder how I managed to mess up things in the first place ; I certainly didn't write anything like ```
chmod 555 ~/Desktop
``` in a terminal....

Anyway, things are once again working perfectly ; now if only **Creative Lab**s would release a 64-bit **Linux** driver for their **SB X-fi** card !...

Henri

---

### Post by heimo on 2007-05-12
> **mhenriday said:**
> *Paljon kiitoksia*, **heimo** !

Tack tack, Henri. :D

---

