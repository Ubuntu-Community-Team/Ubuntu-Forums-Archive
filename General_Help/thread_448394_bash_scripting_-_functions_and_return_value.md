---
title: "bash scripting - functions and return value"
date: 2007-05-19
forum: General Help
---

### Post by bnuytten on 2007-05-19
I am currently working on improving some init scripts. Please have a look at this simple script. The foobar function simply returns its first argument, which is printed.
```
foobar ()
{
        return $1
}
foobar 0
echo A$?
foobar 1
echo B$?
```

If I run the script I get the following output:
```
+ foobar 0
+ return 0
+ echo A0
A0
+ foobar 1
+ return 1
```

So, why is it that when return any other value than 0 from the function stops the execution of the script? If "exit" would have been called in stead of "return" I would understand this behaviour.

Second part of the question: how do I return values (different from 0) from a function, without the complete script to exit?

---

