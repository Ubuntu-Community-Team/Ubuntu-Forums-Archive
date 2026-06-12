---
title: "fdisk in a shell script?"
date: 2008-03-22
forum: General Help
---

### Post by Gerlads Mod on 2008-03-22
I need to run the following commands in fdisk:
```

d
u
n
p
1
489
<enter>
t
c
a
1
w

```

How would I put this in a shell script?

Thanks for your help.

---

### Post by Gerlads Mod on 2008-03-22
Anyone?

---

### Post by beren.olvar on 2008-03-22
try wrtiting your input in a file then
```

$fdisk < filename

```
i would try first with some combination that doesnt actually do anything, and if it works fine try the actual input you need

cheers

---

### Post by mrsteveman1 on 2008-03-22
You still have to specify a device to operate on when you do that:

```
fdisk /dev/sda < fdisk.commands
```

---

### Post by Gerlads Mod on 2008-03-23
Cool I got it to work!
I just put:
```

d
u
n
p
1
489

t
c
a
1
w
```
in a file called command and used **fdisk /dev/sdb < command** to use it.

Thanks a lot guys.

---

