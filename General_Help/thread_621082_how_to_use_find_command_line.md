---
title: "how to use find command line"
date: 2007-11-23
forum: General Help
---

### Post by taisao on 2007-11-23
hello,

when I try to find files that match some patterns with the find command. Beginning from the / location, running as a user, I get many (warning/error) message that I don't want to see. Message is kind like this: ```
find: /proc/9479/task/9479/fd: Permission denied
```

How do I disable that kind of warning? some usefull options with find command or make use of grep command?

---

### Post by taurus on 2007-11-23
```
**sudo** find / -name *whatever_you_want_to_search* -print
```

---

### Post by drs305 on 2007-11-23
It would be helpful to see the command you are typing. 

Some of the information on options can be found by typing:
```
man find
```

---

### Post by ukripper on 2007-11-23
you need to use sudo to have permission access to /proc so just issue
```
sudo 
``` in front of command

---

### Post by misconfiguration on 2007-11-23
You must use sudo in order to search secured directories. 

```
sudo find / -name "~fd" -print
```

to make use of grep, say we know which DIR fd resides.

```
sudo find /proc -name "fd" -print 
```

If you just do a find on the root of a directory or / in general find will look in all partitions for the 'wild card' you've entered.

Another useful tool is du and locate

locate <file_you_want_to_find> (after you run updatedb)

---

### Post by taisao on 2007-11-23
I just want to search for some files as a normal user, and I don't want warning message for the things that I can't access. Using sudo work, but I want to run the command as normal user.

---

### Post by hellion0 on 2007-11-23
Then you'll have errors. "find" searches the ENTIRE filesystem, including areas your normal user isn't meant to see.

---

### Post by ukripper on 2007-11-23
> **taisao said:**
> I just want to search for some files as a normal user, and I don't want warning message for the things that I can't access. Using sudo work, but I want to run the command as normal user.

Normal user can only search normal files under home directory or /tmp
[B]
 NOT RECOMMENDED[/B]  ----- If you are forced to have acces to them you can change permissions of that directory using chmod or chown[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by timcredible on 2007-11-23
you may want to use locate instead. 
```
 locate <search pattern>
```

you may want to update locate's database first:
```
sudo updatedb
```

---

### Post by ukripper on 2007-11-23
*"I just want to search for some files as a normal user, and I don't want warning message for the things that I can't access. Using sudo work, but I want to run the command as normal user."*

Do you hate sudo?

---

### Post by misconfiguration on 2007-11-23
I know I hate it.. It's just hard to remember to use is, especially when 99% of my workload involves being  root on HP-UX and AIX systems.

---

### Post by taisao on 2007-11-23
> **ukripper said:**
> *"I just want to search for some files as a normal user, and I don't want warning message for the things that I can't access. Using sudo work, but I want to run the command as normal user."*

Do you hate sudo?

not really. But we can't always be superuser.

--

I remember reading something about redirect stderr. And the solution is
```
2>/dev/null
```

example:
> find / -iname "*ark*.desktop" 2>/dev/null

that's what I used to find the ark service menu item for konqueror file manager, so I can remove it from the konqueror context menu (right click menu).

item is
```
/usr/share/services/ark_plugin.desktop
```

just remove it or rename it
> sudo mv /usr/share/services/ark_plugin.desktop /usr/share/services/ark_plugin.desktop.old <- (need to use sudo :popcorn: )

---

