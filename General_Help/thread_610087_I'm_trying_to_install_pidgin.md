---
title: "I'm trying to install pidgin"
date: 2007-11-11
forum: General Help
---

### Post by watkinsted on 2007-11-11
I'm trying to install pidgin-2.2.2 and have all I need for the install, but when I type make this is what I get, can anyone help me plz?   

Use kerberos 4 with zephyr.... : no
Use external libzephyr........ : no
Has you....................... : yes

Use XScreenSaver Extension.... : no
Use X Session Management...... : yes
Use startup notification...... : no
Build with GtkSpell support... : no

Build with plugin support..... : yes
Build with Mono support....... : no
Build with Perl support....... : no
Build with Tcl support........ : no
Build with Tk support......... : no

Print debugging messages...... : no

Pidgin will be installed in /usr/local/bin.

configure complete, now type 'make'

ted@ted-desktop:~/pidgin-2.2.2$ make
bash: make: command not found
ted@ted-desktop:~/pidgin-2.2.2$

---

### Post by bakeneko on 2007-11-11
You probably want to install the **build-essential** package, which depends on make, gcc, and the standard c libraries.

---

### Post by watkinsted on 2007-11-11
I believe i've installed from this source before, but what do you mean by build-essential?

---

### Post by kd7swh on 2007-11-11
build-essential has the make application in it.

you need to install make, or you can't compile source.

```
sudo apt-get install build-essential
``` or
```
sudo apt-get install make
```

---

