---
title: "[SOLVED] Clear file contents command"
date: 2007-10-14
forum: General Help
---

### Post by nooblot on 2007-10-14
In Debian Reference file:///usr/share/doc/Debian/reference/ch-tips.en.html¨
I come across a command I never knew about:


> 
8.6.33 Clear file contents

In order to clear the contents of a file such as a logfile, do not use rm to delete the file and then create a new empty file, because the file may still be accessed in the interval between commands. The following is the safe way to clear the contents of the file.

   **  $ :>file-to-be-cleared**



Can someone explain abit more about this command [SIZE="4"]¨:>¨[/SIZE]  ?
What does ¨:¨ stand for in shell ?
How long has this been around ?

thanks

---

### Post by milosz.galazka on 2007-10-14
from *man bash*
```
     : [arguments]
              No  effect;  the command does nothing beyond expanding arguments
              and performing any specified redirections.  A zero exit code  is
              returned.

```

---

### Post by nooblot on 2007-10-14
> No  effect;  the command does nothing.....

well the man page is not quite right there then since it NULL out the file.....

---

### Post by milosz.galazka on 2007-10-14
> **nooblot said:**
> well the man page is not quite right there then since it NULL out the file.....

This builtin command returns nothing to its output. So if you redirect it to file it will be empty.
Return code is always 0 (*echo $?* after executing  *:* command)

---

### Post by nick_h on 2007-10-14
Interesting - I didn't know that one.

Is it any different to:
```
cat /dev/null > file-to-be-cleared
```?

---

### Post by milosz.galazka on 2007-10-14
Results are the same. But I didn't checked source to see how it really works.

---

### Post by cwaldbieser on 2007-10-14
> **nick_h said:**
> Interesting - I didn't know that one.

Is it any different to:
```
cat /dev/null > file-to-be-cleared
```?

You can also do
```

$ > file-to-be-cleared

```

---

