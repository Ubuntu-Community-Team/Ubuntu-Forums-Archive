---
title: "Task Ordering"
date: 2007-04-12
forum: General Help
---

### Post by webworldx on 2007-04-12
Hi everyone!

I'm basically looking for a way to carry out terminal tasks one after another.  I want to run tovid automatically one after another encoding certain files, and obviously I can't run them all together or my laptop would grind to a halt!  So basically, I want some way of telling ubuntu:

run this:
tovid -dvd -pal -in SOMEFILE -out SOMEFILE
then once it's finished, moved on to
tovid -dvd -pal -in SOMEOTHERFILE2 -out SOMEOTHERFILE2
and so on, with me setting a list of all the actions I want it to carry out after each one completes

Any ideas if there's a program available that does this sort of thing already?

Thanks a lot!

---

### Post by ewankho on 2007-04-14
Maybe you can just string the commands together:
  command1;command2
or pipe them if you need the output of the first command as input to the next command:
  command1|command2

---

### Post by 23meg on 2007-04-14
If you separate the commands with "&&", it will tell the shell to execute the second command on the condition that the first has completed successfully.

---

### Post by jfinkels on 2007-04-14
You can make a shell script can't you? Don't they perform commands in order?

```

#!/bin/bash
command1
command2
command3

```
etc. I guess, if that doesn't work for you, and you want to split them up into different files, you could have each command in its own file, let's sayed named "cmd1.sh", "cmd2.sh", etc., and then have them set up like this:
```

#!/bin/bash
#
## cmd1.sh
## This is the file for command1
command1
...
bash cmd2.sh

```
and cmd2.sh will look like 
```

#!/bin/bash
#
## cmd2.sh
## This is the file for command2
command2
...
bash cmd3.sh

```
so they will call each other sequentially. That's poor programming but whatever.

---

### Post by webworldx on 2007-04-14
Thanks 23meg, that's great!

---

