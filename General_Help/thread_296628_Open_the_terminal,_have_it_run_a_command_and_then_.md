---
title: "Open the terminal, have it run a command and then stay open"
date: 2006-11-09
forum: General Help
---

### Post by bruenig on 2006-11-09
I am trying to open a terminal have it run a command and stay open, generally it will open run the command and then close
```
xfce4-terminal -x ls ~
```
will open the terminal list the contents of ~ and then close, I am trying to get it to stop closing

---

### Post by 23meg on 2006-11-09
Append "read" to the end of the script you run with the terminal or launch it with a specific profile, like this ```
gnome-terminal --window-with-profile=[your profile name] -e=[your commands]
```and in that profile, choose the "Keep terminal window open" option.

The latter may not apply to xfce4-terminal.

---

### Post by kerry_s on 2006-11-09
use " -hold " here's how have it used on my actions menu in thunar. if that command don't work use> gnome-terminal -h <to see what the commands are.

xterm -hold -e  md5sum %n

---

### Post by bruenig on 2006-11-09
yeah the hold thing is working sort of for xfce4-terminal it was
xfce4-terminal -H -e ls
the only problem is, and this is not too big a deal, is that while it opens the terminal and then executes the command and stays open, it does not allow for me to run anymore commands from that terminal. I have to either open a tab or another terminal to be able to run commands.

---

### Post by dcstar on 2006-11-09
> **bruenig said:**
> yeah the hold thing is working sort of for xfce4-terminal it was
xfce4-terminal -H -e ls
the only problem is, and this is not too big a deal, is that while it opens the terminal and then executes the command and stays open, it does not allow for me to run anymore commands from that terminal. I have to either open a tab or another terminal to be able to run commands.

Put a "&" at the end of the command line (which means execute the command in background):
```
xfce4-terminal -H -e ls &
```

---

### Post by bruenig on 2006-11-10
> **dcstar said:**
> Put a "&" at the end of the command line (which means execute the command in background):
```
xfce4-terminal -H -e ls &
```

Same result as before, not able to run any more commands from the terminal that is opened.

---

### Post by kerry_s on 2006-11-10
When i was looking into that hold thing for me, i saw i think, a wait command that tells it to wait for input. Try looking into that, i don't have gnome-terminal so i can't check for you, i just use the simple xterm that comes in all linux distro's, so i know the same commands work when i switch to my others.

---

### Post by brentoboy on 2007-05-17
I imagine that the original poster is no longer interested, but I was trying to do the same thing, and here is what I have come up with that works (it seems to me that all the stuff posted here doesnt answer the real question ... run a command, and then leave the term window open, ready to take another command.)

first, some background.
it appears that, if you dont specify the -e <command> then it defaults to /bin/bash (or some other shell -- probably the user default)  anyway, the term window runs one single program.  if it executes your custom command line, there is no bash shell running to exit out to...

so I made a script:
~/hello-world.sh

```

#! /bin/sh

echo "Hello World"
/bin/bash

```

the script runs my command (in this case, echo "hello world") and then opens a bash shell.

now, when I run this command:

```

xterm -e sh ~/hello-world.sh

```

(note, the "sh" command is to run the shell script becuase I am too lazy to change the execute bit in the permissions so it can run itself)

It displays this:

```

Hello World
brent@amd64:~$ _

```

Now, that is fine, unless you want to run one of  several arbitrary commands before exiting to a prompt, and want to avoid making a custom shell script for each one.  In which case, you could make a shell script that takes the desired command as a parameter.  If you do this, make sure and put the command to be run in a paramter

I created a new file
~/run-cmd
This time I set the execute bit
here are the contents:
```

#! /bin/sh

"$1"
/bin/bash

```

and when I run this....
```
xterm -e ~/run-cmd ls
```
I get my directory listing followed by a prompt.

-hope that helps people in the future who have this question.

also, if anyone knows a better / cleaner way -- please post.
Especially if you know a way to let the second "run-cmd" solution be more parameter friendly. (%1 only works if you don't want to send the inner command any parameters.)

-cheers

---

### Post by brentoboy on 2007-05-17
ok, I changed the ~/run-cmd file to this...
```

#! /bin/sh

$1 $2 $3 $4 $5 $6 $7 $8 $9 $10 $11 $12 $13 $14
/bin/bash

```

it will now run commands with their own switches / parameters

Is there a better way to do that?  it seems kind of sloppy the way it is.  having 14 parameters seems wasteful when usually only 1 or 2 is plenty , but at the same time, a program could want more.  Is there a way to be more elegant than that?

just wondering, this works for my purposes, and would probably work for anything anyone else wanted to do with it.

---

### Post by 13u11fr09 on 2007-05-17
> **brentoboy said:**
> ok, I changed the ~/run-cmd file to this...
...
Is there a better way to do that? 


use $@ to reference every parameter:
```

#!/bin/sh

$@
/bin/bash

```

here's a great beginners guide to bash scripting:

[http://www.freeos.com/guides/lsst/]("http://www.freeos.com/guides/lsst/")

here's the referrence to parameters:

[http://www.freeos.com/guides/lsst/ch02sec13.html]("http://www.freeos.com/guides/lsst/ch02sec13.html")

---

### Post by brentoboy on 2007-05-17
thanks a bunch.. I knew there was a better way...

---

### Post by ulrick13 on 2007-11-07
Thanks a lot, it really saved my day. :popcorn:

BTY, does someone knows how to make it work with gnome-terminal instead of xterm ?

Thanks
A+

---

### Post by Ajinomoto on 2007-11-07
A querry from newbie user of Linux/Ubuntu:

how can I run applications(open office)/programs/accesories (calculator/cd volume) in the command line? 

thanks!

---

