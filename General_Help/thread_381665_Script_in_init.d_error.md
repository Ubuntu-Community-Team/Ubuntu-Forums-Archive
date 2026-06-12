---
title: "Script in init.d error"
date: 2007-03-11
forum: General Help
---

### Post by hegyre on 2007-03-11
Hi everybody,

I've this script :

```
#!/bin/bash

cd /boot/grub/splashimages
nbr=$(find -name \[0-9]* | wc -l)
rnd=$((RANDOM%$nbr))
cd /boot/grub
sed -e s/[0-9]*.xpm.gz/$rnd.xpm.gz/g menu.lst > menu.lst.temp
cp menu.lst.temp menu.lstdoe
#rm menu.lst.temp

```

It works fine when i run it manually, but when the init.d run it at boot time, it doesn't work and i get this error message in /var/log/boot :
```
Mar  7 21:53:01 rc2: /etc/rc2.d/S20grub_random_image.sh: 5: arith: syntax error: "RANDOM% 15"
```

or with this command : ```
let "rnd = RANDOM % nbr"
```

i get this : 
M```
ar  8 21:57:54 rc2: /etc/rc2.d/S20grub_random_image.sh: 5: let: not found
```

How do you explain that it works when i run it manually but error when it run at boot time ?
Someone can help me plz ? Thanks in advance

---

### Post by yabbadabbadont on 2007-03-11
I always thought that it was "$RANDOM".

---

### Post by hegyre on 2007-03-11
ok thx but i want a random number between 0 and $nbr, for exemple between 0 and 15

---

### Post by yabbadabbadont on 2007-03-11
> **hegyre said:**
> ok thx but i want a random number between 0 and $nbr, for exemple between 0 and 15

```
randomnumber=`expr $RANDOM % 16`
```

Edit:  If I remember correctly, RANDOM is limited to 32K, in case you needed larger numbers.  I did, so I wrote a quick and dirty program to produce random numbers.

---

### Post by hegyre on 2007-03-12
OK thanks, but it doesn't work in init.d, but i solved the problem

I lauch it with gnome startup programs ^^

---

