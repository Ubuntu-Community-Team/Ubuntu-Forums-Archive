---
title: "Bit of bash script help."
date: 2008-01-02
forum: General Help
---

### Post by PinkFloyd102489 on 2008-01-02
I have a .rar file that I need to open but I dont remember the exact password on it. I remember the word part of it, but there were two numbers attached at the end of it. Instead of trying 10-99 by hand, I was going to make a bash script that would execute the rar command on the archive and enter the password.

My problem is that I cant get the script to "enter" the password. I tried this:

```

#!/bin/bash

rar e name-of-archive.rar
echo "password10"
exit 1

rar e name-of-archive.rar
echo "password11"
exit 1

```

The thing is, it doesnt work. I have to manually enter the password and then it echoes what it's supposed to. Any way I can fix this?

---

### Post by Borbus on 2008-01-02
Well I've never used rar.. but it would need to have some way to input the password with cli, check man rar to see if it has a password option. You should use a loop to do it too.

---

### Post by PinkFloyd102489 on 2008-01-02
Ive already checked the man pages. The only thing I can find is the switch to encrypt the file. Quite the opposite of what I want. :-p

---

### Post by Borbus on 2008-01-02
It probably doesn't have this option then, and probably to stop this very thing!

---

### Post by mali2297 on 2008-01-02
From the man page for unrar-free:
```

       -p<password>
              Set password.

```

---

### Post by PinkFloyd102489 on 2008-01-02
> **mali2297 said:**
> From the man page for unrar-free:
```

       -p<password>
              Set password.

```

That's to set a password, last I checked. I'll try it though.

---

### Post by PinkFloyd102489 on 2008-01-02
I tried it and it works. Thanks!

---

### Post by PinkFloyd102489 on 2008-01-02
One more question. Is there a way I can set a variable for the double digit number and then increment it if the password fails?

---

### Post by Borbus on 2008-01-02
[http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-7.html](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-7.html)

Look at the C-like for. You would do something like this I think:
```

#!/bin/bash
for i in `seq 10 99`;
 do
        rar -p password$i e name-of-archive.rar
done

```

---

