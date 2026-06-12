---
title: "Escaping symbols in PS1 confuses bash in utf-8 directories"
date: 2007-09-26
forum: General Help
---

### Post by 0x656b694d on 2007-09-26
Hi,

If i cd to a directory containing utf-8 characters in its name, my colored bash prompt breaks the further line.

Just a simple example.
```
PS1="\w\$ "
```
That works great! Without colors though.
But adding escape sequences after \w...
```
PS1="\w\[\033[00m\]\$ "
```
...makes the further command line weird &#8212; spaces after $ and after each symbol i enter:
```

$ PS1="\w\[\033[00m\]\$ "
~$ cd /media/Multimedia/&#1052;&#1086;&#1080;\ &#1076;&#1086;&#1082;&#1091;&#1084;&#1077;&#1085;&#1090;&#1099;/
/media/Multimedia/&#1052;&#1086;&#1080; &#1076;&#1086;&#1082;&#1091;&#1084;&#1077;&#1085;&#1090;&#1099;$      c     d           .     .
/media/Multimedia$ echo ok

```

The fun is that \n fixes it:
```

/media/Multimedia$ PS1="\w\[\033[00m\]\n\$ "
/media/Multimedia
$ cd &#1052;&#1086;&#1080;\ &#1076;&#1086;&#1082;&#1091;&#1084;&#1077;&#1085;&#1090;&#1099;/
/media/Multimedia/&#1052;&#1086;&#1080; &#1076;&#1086;&#1082;&#1091;&#1084;&#1077;&#1085;&#1090;&#1099;
$ echo ok

```
Works fine, but i don't want to have a new line.

Is it a known issue? How do i solve this?

Thanks!
-Mike

---

### Post by 0x656b694d on 2007-09-30
The bug has gone with the upgrade to Gutsy.

Cheers!
-Mike

---

