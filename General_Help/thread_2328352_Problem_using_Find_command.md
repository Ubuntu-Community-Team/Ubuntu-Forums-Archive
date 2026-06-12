---
title: "Problem using Find command"
date: 2016-06-20
forum: General Help
---

### Post by peter1897 on 2016-06-20
I did this search 'sudo find / -name ssh' and this is the result i got:

```
max@ubuntu:~$ sudo find / -name ssh
/etc/init.d/ssh
/etc/default/ssh
/etc/ssh
/usr/lib/apt/methods/ssh
/usr/bin/ssh
/usr/share/bash-completion/completions/ssh
```

But i have a ssh folder in my home directory ~/.ssh which the Find command didn't find. Why it didn't find this folder?

---

### Post by howefield on 2016-06-20
How about 

```
sudo find / -name *ssh
```

---

### Post by peter1897 on 2016-06-20
Yes, this way it works.

---

### Post by steeldriver on 2016-06-20
It's usually a good idea to escape or quote special characters in find predicates - otherwise they may get expanded by the shell **before **being passed to `find`, resulting in further head scratching

```

sudo find / -name '*ssh'

sudo find / -name \*ssh

```

---

### Post by Habitual on 2016-06-20
name ssh ! = **[COLOR=#ff0000].[/COLOR]**ssh, 
```
sudo find / -iname '*ssh"
```
or use another provided alternative.

---

### Post by peter1897 on 2016-06-20
> **steeldriver said:**
> It's usually a good idea to escape or quote special characters in find predicates - otherwise they may get expanded by the shell **before **being passed to `find`, resulting in further head scratching

```

sudo find / -name '*ssh'

sudo find / -name \*ssh

```

Is it possible to set the depth of characters for wildcard sign, for example, to 1? So, if i use the command *sudo find / -name '*ssh'* and i have these folders  *assh * and *aassh* it will find the folder* assh, * but not the folder *aassh*.

---

### Post by steeldriver on 2016-06-20
You can use ? to represent a single character, ?? to represent exactly 2 unknown characters and so on

```

sudo find -name '?ssh'

```

(note that this won't find the case with *zero *leading characters, i.e. plain `ssh`, which '*ssh' will)

If you want significantly more complex cases, you'd probably want to switch to regular expression matches ('find -regex ... ') in place of simple globs

---

### Post by peter1897 on 2016-06-20
It works, but i guess if i want to find also the plain 'ssh' along with '?ssh' i have to use regex.

---

