---
title: "windows DOS is to .batch as linux terminal is to....?"
date: 2013-05-30
forum: General Help
---

### Post by iScience on 2013-05-30
okay so, i'm trying to make a file that contains the following line of code

```


$ export ROOTSYS=$HOME/root

$ export PATH=$PATH:$ROOTSYS/bin

$ export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:$ROOTSYS/lib


```

i downloaded a program called "root". Yes, the software itself is called "root". No, i'm not a complete noob referring to the root user.
This is a CLI based program and after installing it, i must enter in these three lines of code above every time i open up a new terminal. After i type those in, i can just type in...

```


$ root


```

and the program starts up.

What i am wanting to do is make a nano file such that i can just type in "root" and those three previous lines of code will automatically be executed. how can i do this?

---

### Post by The Cog on 2013-05-30
Try this - create a file ~/bin/root with the following contents:
```

#!/bin/sh
export ROOTSYS=$HOME/root
export PATH=$PATH:$ROOTSYS/bin
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:$ROOTSYS/lib
$ROOTSYS/bin/root

```
Now make it executable with this command:
```
chmod +x ~/bin/root
```
typing the command root should now run this little script which calls the real root program.

---

### Post by iScience on 2013-05-30
thank you very much!!

---

