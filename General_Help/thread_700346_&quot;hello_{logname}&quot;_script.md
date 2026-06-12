---
title: "&quot;hello {logname}&quot; script?"
date: 2008-02-18
forum: General Help
---

### Post by secondstage on 2008-02-18
brand new to writing scripts, and got the idea ,instead of 
code:

#!/bin/bash
echo "Hello World!"

is it possible to have the variable of logname in place of world
basically, can there be a command within the echo?

---

### Post by harold4 on 2008-02-18
```
echo `whoami`
```

---

### Post by seventhc on 2008-02-18
```

j0hn@cipher:~$ echo 'whoami'
whoami

```
lol nevermind they are back ticks not quotes.. :D
```

j0hn@cipher:~$ echo `whoami`
j0hn

```

---

### Post by secondstage on 2008-02-18
does that work for any command within echo?

---

### Post by Subliminal Aura on 2008-02-18
> **secondstage said:**
> does that work for any command within echo?

Yes the backticks ` ` enclose a system call to another command

Try 

echo "Number of users logged in `who | wc -l`"

---

