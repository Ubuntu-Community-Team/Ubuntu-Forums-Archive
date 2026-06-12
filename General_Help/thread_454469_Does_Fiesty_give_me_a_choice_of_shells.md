---
title: "Does Fiesty give me a choice of shells?"
date: 2007-05-25
forum: General Help
---

### Post by timdoc1 on 2007-05-25
What's your favorite?

---

### Post by dbott67 on 2007-05-25
I can honestly say that I've only used bash (although dash was the default in Edgy).

Anyhow, for those that want to know what shell they're using, which ones are available and how to change it, here are a few commands:

To view your current shell:
```
dbott@feisty:~$ [COLOR=Red]**echo $SHELL**[/COLOR]
/bin/bash
```
To see a list of available shells:
```
dbott@feisty:~$ [COLOR=Red]**cat /etc/shells**[/COLOR]
# /etc/shells: valid login shells
/bin/csh
/usr/bin/es
/usr/bin/ksh
/bin/ksh
/usr/bin/rc
/usr/bin/tcsh
/bin/tcsh
/usr/bin/esh
/bin/false
/bin/false
/bin/false
/bin/false
/bin/false
/bin/false
/bin/sh
/bin/bash
/bin/rbash
/bin/dash
/usr/bin/screen
```
To change your default shell:
```
dbott@feisty:~$ **[COLOR=Red]chsh[/COLOR]**
Password:
Changing the login shell for dbott
Enter the new value, or press ENTER for the default
        Login Shell [/bin/bash]:

```

---

