---
title: "update manager errors (please help...)"
date: 2007-07-15
forum: General Help
---

### Post by thesonisshining on 2007-07-15
i tried to update my system a few minutes ago and i got this error

```
'E:Type '“deb' is not known on line 46 in source list /etc/apt/sources.list, E:The list of sources could not be read.'
```

how do i fix this?

---

### Post by McNils on 2007-07-15
It looks like you have a line  (47) in /etc/apt/sources.list that is double quoted. Remove them.

sudo gedit /etc/apt/sources.list

---

### Post by thesonisshining on 2007-07-15
i just tried to but it is saying that i don't have privileges. it says i need to be root. so how do i login as root?

---

### Post by McNils on 2007-07-15
Well the **sudo** command should grant you root privileges.
Try this:
Alt-F2
type in gksudo gedit /etc/apt/sources.list

gksudo is  the same thing as sudo but with a grapical interface.

---

### Post by thesonisshining on 2007-07-15
i did that and clicked run but it didn't do anything.

---

### Post by McNils on 2007-07-15
Open a terminal an type:
sudo nano /etc/apt/sources.list

---

### Post by thesonisshining on 2007-07-15
ok i ran it through terminal (alt+F2 was the run application window) and it let me try to update but now i got this error

```
W: GPG error: http://packages.dfreer.org feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D4C9CD8F7572013D

```

how do i fix this?

---

### Post by thesonisshining on 2007-07-15
i just clicked past that error and now i got this one also.

```
W: Failed to fetch http://wine.budgetdedicated.com/apt/pool/main/w/wine/wine_0.9.41~winehq0~ubuntu~6.10-1_i386.deb
  
```

---

### Post by thesonisshining on 2007-07-15
ok well i don't understand the wine error because i tried it again and it installed fine; but the first error is still occurring.

---

### Post by thesonisshining on 2007-07-15
btw i removed the quotes.

---

### Post by McNils on 2007-07-16
> **thesonisshining said:**
> ok i ran it through terminal (alt+F2 was the run application window) and it let me try to update but now i got this error

```
W: GPG error: http://packages.dfreer.org feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D4C9CD8F7572013D

```

how do i fix this?

You should install the public key. I do not know how tho to this and I do not know where you can find it. Sorry.

---

