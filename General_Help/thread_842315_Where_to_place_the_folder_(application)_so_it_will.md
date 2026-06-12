---
title: "Where to place the folder (application) so it will be shared by all users?"
date: 2008-06-27
forum: General Help
---

### Post by adhg on 2008-06-27
Hello,

   By now, I have 3 users using the same computer with ubuntu. I would like to install an application that would be shared by everyone (eclipse - Java development); my question is this: WHERE should I place the specific folder so it can be shared by all users.

thank you!

---

### Post by Taxman415a on 2008-06-27
/usr/local/bin is the standard place to put local executables that aren't part of a standard system install as it is in everyone's path by default. But if you're asking about where to install eclipse itself, I'd recommend going with that the packages itself uses unless you know better. In other words, just go with sudo aptitude install ecplise and so on or if you're installing a newer version find that deb and install that.

---

### Post by chrisccoulson on 2008-06-27
Can't you just install it from the repositories? Open a terminal and type:
```
sudo apt-get install eclipse
```
It will install Eclipse with the java development tools, and all users will be able to use it. There are other Eclipse plugins in the repositories as well

---

