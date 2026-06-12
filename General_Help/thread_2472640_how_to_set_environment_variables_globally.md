---
title: "how to set environment variables globally ?"
date: 2022-03-07
forum: General Help
---

### Post by vincentberenz on 2022-03-07
According to some posts I found online, the "export" keyboard should be used.

But if I type in a terminal:

```
export foo="foo"
```

and then, in a new terminal:

    ```
echo $foo
```

nothing is printed.

I am in ubuntu 20.04.1

---

### Post by Impavidus on 2022-03-07
You have to put the command in a file that is read when you start a new shell. There are several of such files: ~/.bashrc, /etc/bash.bashrc, ~/.profile, /etc/profile, /etc/profile.d/*; I probably missed some.

---

### Post by Holger_Gehrke on 2022-03-07
"export" makes variables visible to child processes of the shell in which it was executed. If you started the new terminal from the shell in the old terminal, the variable would be visible.

In addition to the files Impavidus mentioned there's also the directories ~/.config/environment.d/,/etc/environment.d/, /run/environment.d/, and /usr/lib/environment.d/ and the file /etc/environment (in order of descending priority). For details see 'man 5 environment.d'. Variables in *.conf files in these directories will be defined after login during the start-up of the user session.

Holger

---

