---
title: "Which application from which repository?"
date: 2006-10-19
forum: General Help
---

### Post by foxy123 on 2006-10-19
I wonder if there is a way to see from which repository I am going to install a programme? I have so many unofficial repositories in my sources.list that sometimes I do not know if the programme I have installed is available in official Ubuntu repos.

---

### Post by CatKiller on 2006-10-19
If you look at the Properties, and then Versions, you may be able to glean some information about which repository it is from.

---

### Post by angkor on 2006-10-19
To see if it's available in the official repos, you can search here:

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

You can use 'apt-cache show [package] | grep Section' to see from where the package will be installed. eg

```
apt-cache show stellarium | grep Section
Section: universe/science
```

---

### Post by foxy123 on 2006-10-19
thanks guys, but they are both indirect ways...

---

### Post by metalheart on 2006-10-19
Or
```
sudo apt-cache show *package-name*
```

---

