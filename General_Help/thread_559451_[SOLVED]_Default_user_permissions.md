---
title: "[SOLVED] Default user permissions?"
date: 2007-09-25
forum: General Help
---

### Post by Trojan_Neo on 2007-09-25
Hi All,

I have some minor problem which become annoying.....
by mistake i "un-tick" permissions in my own default account. the result is that i don't see under Administration > the folder "User and Group" which was there before

1. I try create new user and change the permissions to admin group but still didn't get anything.
2. I try nano /etc/sudoers and add my name via safe mode in GRUB --->>

%admin ALL=(ALL) ALL
sushi ALL=(ALL) aLL

nothing seems to work.....also i try search for the icon "User and Group" under /etc/...but without any success.....

any suggestion?:mad::mad::mad:

thanks in advance....
Trojan_Neo

---

### Post by Compyx on 2007-09-25
You'll need to do:
```

sudo visudo

```
to be able to edit /etc/sudoers.

---

### Post by zvacet on 2007-09-25
You lost your admin privileges.To bring them back

```
sudo adduser username admin
```

---

### Post by Trojan_Neo on 2007-09-25
Thanks for that :) 
all working normal.....:KS

```
sudo adduser sushi admin
```
all working normal.....:KS
thanks again

---

