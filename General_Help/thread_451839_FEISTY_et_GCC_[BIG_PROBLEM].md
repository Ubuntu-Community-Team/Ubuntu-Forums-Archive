---
title: "FEISTY et GCC [BIG PROBLEM]"
date: 2007-05-22
forum: General Help
---

### Post by dj__farde on 2007-05-22
Hello,

I've got a problem, when i want to compil something when i wrote ```
./configure
```
it returns me this : 
```
checking for prefix by checking for wish... /usr/bin/wish
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
```

**I want to precise** that build essential is already installed and i've got the last version of  GCC (gcc-4.1) 
More or this, it's probably my fault because a few days ago compilation was great !

Please anyone to help me?

---

### Post by cborga1985 on 2007-05-22
try this in the terminal```
sudo aptitude purge build-essential
sudo aptitude install build-essential
```and then run ./configure again

---

### Post by DoktorSeven on 2007-05-22
If that doesn't work, check config.log as it says (it's in the same directory as the configure); it should give you the specifics of what went wrong (that you can paste here).

---

### Post by dj__farde on 2007-05-23
In my log i can see this  : ```
gcc: error trying to exec 'cc1': execvp: No such file or directory
```

And when i try to compil a basic program it returns me the same error!
More of this when i do a```
 find /usr/ -name cc1 2> /dev/null
``` normally it will return 
```
/usr/lib/gcc/i486-linux-gnu/4.1.2/cc1
``` but on my case nothing.

---

### Post by veerakumar on 2007-05-23
Your GCC installation is damaged.
Re-install GCC with feisty or by hand.

---

### Post by dj__farde on 2007-05-23
I just did a purge and install of build essential.
The system tell me that all its done

But the same problem! :(

---

