---
title: "Linking and Renaming"
date: 2006-11-13
forum: General Help
---

### Post by PeopleEater on 2006-11-13
I have recently been packaging the buuf icon set for myself for gnome 2.16 and have ran into a problem when I renamed the folder they were in. This causes all the links I've made using **ln -s** to break.

So my question is how do you make a link that will not break if the folder it is in is renamed.

---

### Post by earobinson on 2006-11-13
as far as I know you cant do this in windows or linux. the only thing you could do (and im not sure it would work since im not at my linux box) is to link to stuff inside the dir

eg if you have a dir named foo and inside foo you have 3 links if they where made using the relative instead of the absolute path they should work when foo is renamed

Sorry but Its not possible for hard paths to auto change as far as I know.

---

### Post by PeopleEater on 2006-11-13
Actually that helped a lot all I was doing was linking icons together in the same directories to save some space. I guess I was just doing the easy way of dragging the files into my terminal from nautilus. Thanks.

---

