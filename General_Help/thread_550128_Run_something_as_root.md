---
title: "Run something as root?"
date: 2007-09-13
forum: General Help
---

### Post by Christ_Guard on 2007-09-13
How do I run an .SH file as "Root" from the terminal?

---

### Post by reckless2k2 on 2007-09-13
sudo thefile.sh

---

### Post by Maestro23 on 2007-09-13
> **Christ_Guard said:**
> How do I run an .SH file as "Root" from the terminal?

Use "sudo" in front of your commands.

RootSudo: [https://help.ubuntu.com/community/RootSudo?highlight=%28RootSudo%29](https://help.ubuntu.com/community/RootSudo?highlight=%28RootSudo%29)

---

### Post by tszanon on 2007-09-13
> **reckless2k2 said:**
> sudo thefile.sh
Shouldn't it be
```
sudo **./**thefile.sh
```
?

---

### Post by Maestro23 on 2007-09-13
chmod +x filename.sh (make executable)

./filename.sh

---

### Post by Maestro23 on 2007-09-13
> **tszanon said:**
> Shouldn't it be
```
sudo **./**thefile.sh
```
?

Yeah, might have to do a 

chmod +x filename.sh (make it executable) first.

---

### Post by tvrg on 2007-09-13
or sudo sh thefile.sh, that runs thefile.sh through sh, withtout the need to make it executable as sh is already executable

hope i'm not to unclear

---

### Post by Maestro23 on 2007-09-13
> **tvrg said:**
> or sudo sh thefile.sh, that runs thefile.sh through sh, withtout the need to make it executable as sh is already executable

hope i'm not to unclear

That works to. :smile:

---

