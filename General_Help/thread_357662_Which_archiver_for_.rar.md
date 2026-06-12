---
title: "Which archiver for .rar?"
date: 2007-02-09
forum: General Help
---

### Post by foxmulder881 on 2007-02-09
I have downloaded a .rar compressed file and realized that the default archive manager in Ubuntu will not extract its contents. Which is the best way to extract it?

---

### Post by ~LoKe on 2007-02-09
```
sudo apt-get install unrar
```
```
unrar x file.rar
```

---

### Post by tbroderick on 2007-02-09
Install unrar (multiverse) or unrar-free, but unrar-free doesn't work on all rar's. The archive manager will then be able to extract or use the console commands;
```
unrar x file.rar
```

---

### Post by taurus on 2007-02-09
From a terminal, Applications -> Accessories -> Terminal, unrar it with

```
unrar x **filename.rar**
```

You probably need to enable both universe & multiverse by removing the # in front of all the lines with deb at the beginning in /etc/apt/sources.list.  Then use synaptic and search for unrar package and install it.

```
gksudo gedit /etc/apt/sources.list
sudo apt-get update
```

---

### Post by foxmulder881 on 2007-02-09
Thanks. I'm at work atm, but I'll give it a shot when I get home and let you know.

---

### Post by foxmulder881 on 2007-02-10
I used the terminal script provided by ~LoKe.

Thanks mate. It worked.

---

### Post by ~LoKe on 2007-02-10
> **foxmulder881 said:**
> I used the terminal script provided by ~LoKe.

Thanks mate. It worked.

You're quite welcome.

---

