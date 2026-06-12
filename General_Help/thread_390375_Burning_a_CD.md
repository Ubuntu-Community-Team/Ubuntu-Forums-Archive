---
title: "Burning a CD"
date: 2007-03-21
forum: General Help
---

### Post by rasalibra on 2007-03-21
Why is that i have to run cd burning applications as root for them to work. I try to run k3b or gnome bake but they wont actually burn the cd unless its run from root

---

### Post by taurus on 2007-03-21
Do you belong to group cdrom?  What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
id
```

---

### Post by rasalibra on 2007-03-26
sorry it took a while but this is what i get


josh@Ubuntu:~$ id
uid=1000(josh) gid=1000(josh) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),110(netdev),111(lpadmin),113(powerdev),114(scanner),118(admin),1000(josh)
josh@ubuntu:~$

---

