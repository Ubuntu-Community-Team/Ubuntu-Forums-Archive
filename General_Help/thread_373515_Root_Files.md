---
title: "Root Files?"
date: 2007-03-01
forum: General Help
---

### Post by gmutt on 2007-03-01
.

---

### Post by Maestro23 on 2007-03-01
What are you trying to create in "/"?

---

### Post by gmutt on 2007-03-01
.

---

### Post by llamakc on 2007-03-01
Open a Terminal.

type: 

sudo mkdir /path/to/and/namofdirectory

---

### Post by gmutt on 2007-03-01
.

---

### Post by llamakc on 2007-03-01
> **gmutt said:**
> So in Kubuntu Edgy it would be:  kdesu mkdir /path/to/and/namofdirectory ?

Thanks llamakc

If you are in Konsole, no it would still be just "sudo mkdir /MYDIR or /opt/MYDIR" where /MYDIR would be created directly under /, and /opt/MYDIR would appear inside of /opt.

If you're using the graphical file browser (Konquerer?) I don't know how to do it with root or sudo privilieges. Sorry.

---

### Post by ~LoKe on 2007-03-01
> **llamakc said:**
> If you're using the graphical file browser (Konquerer?) I don't know how to do it with root or sudo privilieges. Sorry.
Alt+F2
```
kdesu konqueror ## or whatever it's called
```
Now you'll be in the file browser as root.

---

### Post by gmutt on 2007-03-01
.

---

