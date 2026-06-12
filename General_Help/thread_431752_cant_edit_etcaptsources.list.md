---
title: "cant edit /etc/apt/sources.list"
date: 2007-05-03
forum: General Help
---

### Post by manizzle on 2007-05-03
so im trying to install vlc player by compiling the source codes i got from a site. in the instalation directions, it said to add some repositories through the /etc/apt/sources.list by editing it. the problem is that i cant edit the file in any way. i have tried chmod to +rwx and still nothing happened, and also chown to me, murtaza, my account, so that i could edit it. i could then edit the file, adding the respository links, but then when i went to save it, i could not. im trying to upgrade my ubuntu and again, i need to edit my sources.list file. any help would be surely appreciated. ive googled, but have gotten nothing yet. thank

-murtaza

---

### Post by Cypher on 2007-05-03
You shouldn't change the permissions on that file..or anything else in /etc..but rather do
```

gksudo gedit /etc/apt/sources.list

```

---

### Post by taurus on 2007-05-03
Please read [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo).

---

