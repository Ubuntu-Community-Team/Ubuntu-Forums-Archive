---
title: "Sudo not working for chmod"
date: 2019-01-18
forum: General Help
---

### Post by qbaqbar on 2019-01-18
I am trying to install a piece of software on a clean AWS instance. It requires changing permissions on a bunch of files. 

The first batch goes ok after 

sudo chmod [COLOR=#208050]644[/COLOR] config.local.php
sudo chmod -R [COLOR=#208050]755[/COLOR] design images var

But when I try to run

sudo find design -type f -print0 | xargs -0 chmod [COLOR=#208050]644[/COLOR] 

I get

chmod: changing permissions of 'design/.htaccess': Operation not permitted


Any ideas what might be wrong?

---

### Post by qbaqbar on 2019-01-18
Oh, running 
ls -l /usr/bin/sudo

shows root permissions of -rwsr-xr-x

---

### Post by CatKiller on 2019-01-19
> **qbaqbar said:**
> But when I try to run

sudo find design -type f -print0 | xargs -0 chmod 644

I get

chmod: changing permissions of 'design/.htaccess': Operation not permitted
That's running find as root rather than running chmod as root.

---

### Post by qbaqbar on 2019-01-19
Hmm, but the error I get is chmod related, right?

---

### Post by Impavidus on 2019-01-19
> **qbaqbar said:**
> 
sudo find design -type f -print0 | xargs -0 chmod [COLOR=#208050]644[/COLOR] 

The pipe separates commands from each other and connects their I/O together. The shell sees two commands here: **sudo find design -type f -print0** and **xargs -0 chmod 644**; and the shell sets up a pipe to feed the standard output from the first command into the standard input of the second. sudo then runs find as root and xargs runs chmod with some extra options, but obviously (as it should be by now) sudo doesn't affect xargs or chmod.

This is one of those cases where I'd use a root shell:```
sudo -i
commands (no sudo required)
exit
```

---

