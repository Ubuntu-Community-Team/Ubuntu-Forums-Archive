---
title: "-su: 31:export: : bad variable name"
date: 2013-10-09
forum: General Help
---

### Post by rufai_mustapha on 2013-10-09
Good day, I was downloading and installing the android developer tools when my computer suddenly shuts down, trying to log in as been a problem. I use the ubuntu 12.04 on an acer c7 chromebook, using the chroot or crouton version that can easily switch from one os to the other. The error I get after typing these normal routine stuff 
$shell
$sudo startunity
the errors are 
-su: 31: export: : bad variable name
help me as a new user, thanks in advance.

---

### Post by Bucky Ball on 2013-10-09
Welcome. Is that a typo? If not, don't you mean:

```
sudo start unity
```
 
I actually don't know that you need the sudo. That would open unity as root. Just:

```
start unity
```

... and see what happens.

---

### Post by rufai_mustapha on 2013-10-09
no, its not a typo, i always use " sudo startunity". and it used to work until this morning when I was logged out. and the " start unity gave a command not found error"

---

### Post by rufai_mustapha on 2013-10-09
I found this out while going through my terminal, I don't know if it will help

"
Welcome to crosh, the ChromeOS developer shell.If you got here by mistake, don't panic!  Just close this tab and carry on.Type 'help' for a list of commands.crosh> shell[COLOR=#00BA13]**chronos@localhost**[/COLOR][COLOR=#729FCF]** / $**[/COLOR] sudo startunityEntering /usr/local/chroots/precise...-su: 31: export: : bad variable nameUnmounting /usr/local/chroots/precise...[COLOR=#00BA13]**chronos@localhost**[/COLOR][COLOR=#729FCF]** / $**[/COLOR] sudo enter-chroot -x su -Entering /usr/local/chroots/precise...-su: export: `=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/opt/android-sdk-linux/tools': not a valid identifier-su: eport: command not found(precise)root@localhost:~# 
"

---

