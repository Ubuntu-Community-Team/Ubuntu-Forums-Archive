---
title: "Syntax for Nautilus-script"
date: 2007-01-26
forum: General Help
---

### Post by patrick_g on 2007-01-26
Hi,

For converting my mp3 in ogg i use mp32ogg in command line.

i have created an alias in bash

```
alias mp32ogg='mp32ogg --quality=4 --delete'
```

But i search a speedier solution a i think about a nautilus-script. With this nautilus-script all i will have to do is to right-clic on a directory and choose my nautilus-script.

I have tried this syntax :

```
#!/bin/bash
#
gnome-terminal --command="mp32ogg --quality=4 --delete"
```

But it does not work !
What is the solution for this problem ?

---

### Post by cmost on 2007-01-26
I'm not a programmer, but offhand I'd say your script does not specify the filename for input to the command you've specified.

---

### Post by patrick_g on 2007-01-26
Humm...yes you are right.
I thought that the right-clic on a directory was enough but obviously it's not the case.

Do you know the syntax to put in the script to deal with a right-clic selected directory ?

---

### Post by cmost on 2007-01-26
Maybe somthing like this:

#!/bin/bash
#
gnome-terminal --command="mp32ogg --quality=4 --delete" $NAUTILUS_SCRIPT_CURRENT_URI

This variable specifies the current directory, so, if you ran this script within this directory you might be able to pass that info to your command.  Just guessing...like I said, i'm no programmer.  Good luck!

---

