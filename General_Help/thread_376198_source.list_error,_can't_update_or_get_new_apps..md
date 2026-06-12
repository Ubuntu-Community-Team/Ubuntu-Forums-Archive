---
title: "source.list error, can't update or get new apps."
date: 2007-03-04
forum: General Help
---

### Post by Spaceomega on 2007-03-04
I've just started using Ubuntu a few days ago, and installed the Feisty Fawn Herd 5 (yes, i know, unstable..But I couldn't get Edgy to work with my WUSB54GC), and it was working fine until about an hour ago, and now when I go in the Add/Remove Programs or Synaptic Manager i get this error.

[IMG]http://i11.tinypic.com/2vb2y5y.png[/IMG]

Does anyone know how/if I can fix this?

---

### Post by caldevil on 2007-03-04
If you are familiar with terminal commands can you post the output of

sudo apt-get update

---

### Post by Spaceomega on 2007-03-04
E: Malformed line 2 in source list /etc/apt/sources.list.d/feisty-main.list (dist parse)


That's the error code I get after typing "sudo apt-get update" .  Hope it helps.

---

### Post by caldevil on 2007-03-04
Seems like you need to fix the file  /etc/apt/sorces.list.d/feisty-main.list

open the file using gedit and see if you can fix it. Otherwise post the content of the file here.

---

### Post by taurus on 2007-03-04
Put a # in front of second line in /etc/apt/sorces.list.d/feisty-main.list.

```
gksudo gedit /etc/apt/sorces.list.d/feisty-main.list
```

---

### Post by Spaceomega on 2007-03-04
> **taurus said:**
> Put a # in front of second line in /etc/apt/sorces.list.d/feisty-main.list.

```
gksudo gedit /etc/apt/sorces.list.d/feisty-main.list
```




Thanks.


BY THE WAY:  If anyone else has this problem, he messed up in the code.  Small typo :)

```
gksudo gedit /etc/apt/sources.list.d/feisty-main.list
```

---

### Post by taurus on 2007-03-04
Hey, I just cut 'n paste it from caldevil's so...

---

