---
title: "CHMOD - help with restricting read access to home directories"
date: 2007-04-19
forum: General Help
---

### Post by megamania on 2007-04-19
In short, what I need to do is to change permissions for my home directory (say home/User) so that only Root and User can read/write to it.
Currently, my Guest account can read files in the home/User directory. I don't want that because the Guest account is only used by friends coming here to surf the internet...

I know this may be particularly easy to solve, but last time I played with chmod I managed to make a big mess, so I'm asking for help here.  :-)

---

### Post by taurus on 2007-04-19
Applications -> Accessories -> Terminal
```
cd /home
chmod 700 **username**
```
where **username** is your login name.

---

### Post by megamania on 2007-04-19
> **taurus said:**
> 
chmod 700 **username**

Thanks a lot! It works perfectly!

---

