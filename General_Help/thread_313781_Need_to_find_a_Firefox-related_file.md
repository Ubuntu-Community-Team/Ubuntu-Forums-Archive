---
title: "Need to find a Firefox-related file"
date: 2006-12-06
forum: General Help
---

### Post by navneeth on 2006-12-06
I've been having a problem with an extension known as Tab Mix Plus. Now I need to find this file called **classic.jar**. It is supposed to in the Chrome folder; but there are so many firefox-related and Chrome folders I'm not able find this little file. All I see are .css files in some of them. ](*,) Please help me find this file.

---

### Post by taurus on 2006-12-06
You can use either the locate command or the find command.

Applications -> Accessories -> Terminal
```
locate classic.jar
-or-
sudo find / -name classic.jar -print
```

---

### Post by navneeth on 2006-12-06
Wow! It's that simple...yet to get used to all the commands. Thanks.

If these commands search the entire disk, then that file is not in my Ubuntu. The first one returned nothing, and the second found the classic.jar files of Fx and Tb sitting in the XP paprtition. But the thing is ,before I posted the thread, I searched for older threads with this name, and I could find quite a few them (mainly stuff from the terminal) with locations of this file. But I couldn't that file at those locations. :(

---

