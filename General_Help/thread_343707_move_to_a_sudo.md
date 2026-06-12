---
title: "move to a sudo"
date: 2007-01-21
forum: General Help
---

### Post by shickidyshade on 2007-01-21
Hey guys im trying to move a file into a directory 

the files are located in ~/safepeer 
and they must all be moved to 
sudo opt/azureus/plugins/safepeer
I was able to create the directory :D  but now im lost ](*,) so any help would be greatly appreciated thanks guys

---

### Post by taurus on 2007-01-21
```
sudo mv ~/safepeer/* /opt/azureus/plugins/safepeer
```

---

### Post by aysiu on 2007-01-21
Don't forget you can use drag-and-drop and point-and-click, too, if you Alt-F2 and ```
gksudo nautilus
``` or, if you're using Kubuntu ```
kdesu konqueror
```

---

### Post by shickidyshade on 2007-01-21
do use azureus it keeps asking to update the latest is a swt-3.3M3-I1128-gtk-linux-x86.zip which might have something to do i was wondering where these file shoud be located they are .so files and a .jar file should they be in opt/azureus of a deeper path such as plugins 

also why doesnt azureus install into itself

---

