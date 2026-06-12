---
title: "gksu not working. After edgy update?"
date: 2007-02-03
forum: General Help
---

### Post by kd7swh on 2007-02-03
gksu is not working at all. It acts like I am entering the wrong password. I know the password is correct because it still works with su and sudo. Did something change in a recent edgy update?

PS. I am using bash not dash with edgy.



I take part of that back sudo is not working either.

---

### Post by Paerez on 2007-02-03
try running:
```
sudo dpkg-reconfigure gksu gksudo
```

---

### Post by kd7swh on 2007-02-06
reconfig didn't do anything it just blinks in the console... 

(bump)

---

### Post by taurus on 2007-02-06
What's the output of this command from a terminal?

```
id
```

---

### Post by kd7swh on 2007-02-06
thanks for pointing that out to me. 

gksu works when I added my user to the "root" group. This can't be safe though. 

```
jon@laptop:~$ id
uid=1000(jon) gid=1000(jon) groups=0(root),4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),109(lpadmin),111(scanner),114(admin),1000(jon)

```

---

### Post by taurus on 2007-02-06
You should only use gksudo for GUI apps.  Can you run something like

```
gksudo gedit /etc/apt/sources.list
```
and create a new line with ### on it?  Then, save it.

---

### Post by kd7swh on 2007-02-06
ya, that works fine now that the user is in the root group

---

### Post by taurus on 2007-02-06
The user should never be in the group root, at least not on my system.  Did you change anything in /etc/sudoers?

---

