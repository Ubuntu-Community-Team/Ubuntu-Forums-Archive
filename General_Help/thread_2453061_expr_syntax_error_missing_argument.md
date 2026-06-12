---
title: "expr syntax error missing argument"
date: 2020-11-02
forum: General Help
---

### Post by hoftom on 2020-11-02
Hello guys, i tried this command, but crashed with expr: syntax error: missing argument after '<' 
How to fix it? And it will be usefull if you could tell me what should that command do :D

#!/bin/bash
a=`df --output=pcent /$1 | grep '[0-9]' | sed 's/%//'
b=`expr $a \< $2`
echo $b
exit $b

---

### Post by Holger_Gehrke on 2020-11-02
I put a comment after every line:
```

#!/bin/bash
# shebang; tells the system that this script should be interpreted by /bin/bash
a=`df --output=pcent /$1 | grep '[0-9]' | sed 's/%//'
# get the percentage of used space on the device on which the file given to the script as the first parameter resides; 
# strip off the header (grep does that, it only lets lines containing a digit through) and the percentage sign by using sed
# store the resulting number in a
# The '/' before the '$1' is a bit stupid. For absolute paths this results in '//' which gets treated as a single slash. With no first parameter it will use the root-filesystem. 
# The problem is what happens if you pass a relative path; adding a '/' at the beginning turns it into an absolute path which probably doesn't exist resulting in an error and variable a being empty
b=`expr $a \&lt; $2`
# comparison between a and a percentage passed as the second parameter to the script (returns '1' if a is smaller then the second parameter, 0 otherwise)
echo $b
# show the result of the comparison
exit $b
# exit, setting return value to the result of the comparison

```

You get an error because you probably called the script without any parameters. This should be called with two parameters - an absolute path and a percentage - and will print '1' if there's less than the given percentage of used space on the device the path sits on. Example 'scriptname / 50' will print '1' if less than 50% of the root-device is used. Looks like something that would be found as a helper function in some kind of installation script.

Holger

---

### Post by hoftom on 2020-11-02
Thanks Holger!

---

