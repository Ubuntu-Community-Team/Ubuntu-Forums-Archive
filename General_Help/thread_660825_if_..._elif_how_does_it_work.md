---
title: "if ... elif how does it work??"
date: 2008-01-07
forum: General Help
---

### Post by MalcolmCowen on 2008-01-07
I have a script which is supposed to run straight from the box, but doesn't.

After hacking it down down I get this script

#! /bin/sh   

ls

if  33 = 33; then

 echo aaa;

elif 2 = 1; then

  echo cccc;

fi


Which according to the BASH manual should work.
But instead returns Syntax Error: elif unxpected (expecting "then")

I've also had problems with blank lines giving errors, or the first line not being recognised, although  these seemed to go after cutting and pasting the file to another file with gedit.

Is the Ubuntu shell the Bash shell, or is there something else going on?

---

### Post by mcduck on 2008-01-07
The default shell where /bin/sh points to is Dash, although user shell is Bash.

To make sure your script is run with Bash change the first line to #! /bin/bash.

---

### Post by vanadium on 2008-01-07
You need to delineate the test condition with [ ...] , e.g. if [ 32 = 32 ]

---

### Post by juaka on 2008-01-07
try this

```

#!/bin/sh

ls

if [ 33 -eq 33 ]; then
    echo "aaa";
elif [ 2 -eq 1 ]; then
    echo "cccc";
fi

```i found this guide [http://www.usd.edu/~sweidner/lsst/]("http://www.usd.edu/%7Esweidner/lsst/") looks very complete

---

### Post by rubicon on 2008-01-07
Right,

And, FYI, the whole point of scripting is to make all-shell-compatible scripts. That means, if script runs OK in bash, but does not in dash/zsh/other, _the code_ must be fixed, _not magic_ ("magic" is this comment: ```
#!/bin/sh
```, which gives a hint of what must be used to interpret script file). So, my advice is to try to get the script work with any common shell.
[COLOR="Silver"]
Of course, that doesn't mean you should fix python script so it runs in perl fine :)[/COLOR]

---

