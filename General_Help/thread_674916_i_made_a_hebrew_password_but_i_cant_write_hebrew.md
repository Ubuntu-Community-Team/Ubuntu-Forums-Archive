---
title: "i made a hebrew password but i cant write hebrew"
date: 2008-01-22
forum: General Help
---

### Post by israel102 on 2008-01-22
ok so when i started wubi it asked me to put a password in, and i put it in hebrew. now when i boot ubuntu i have to put that password in but i cant because i cant write hebrew. so does anyone know how to change the typing language (remember i dont have access to the desktop, only the login menu)?
i allready tried changing the language throught the little "options" menu but that didnt work (probably changes the desktop language, not the typing)

im also posting this for admins to change wubi to warn users to type the password in english.

so is there any way to change the typing language or even the password?

 thanx

---

### Post by mrollings on 2009-09-11
You can change the password by logging in as root. In the grub menu there should be a recovery option below the normal boot. If you select this you can login to a root shell.

From there enter
```
passwd username
```
where username is your username, and it will prompt you to enter a new password for your user.

---

### Post by michy99 on 2009-09-11
1) Since he is using a wubi install, he doesn't have the grub menu.

2) The post is from January, 2008.

---

