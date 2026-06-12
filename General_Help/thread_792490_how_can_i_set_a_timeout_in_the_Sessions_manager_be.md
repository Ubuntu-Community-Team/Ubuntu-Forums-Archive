---
title: "how can i set a timeout in the Sessions manager before running a startup program"
date: 2008-05-13
forum: General Help
---

### Post by linuxed on 2008-05-13
In the System > Preferences > Sessions window I need to add a timeout to one of the startup program entries so that it waits about 10 seconds before it's actually executed.  Is this possible?

Example:
timeout(wait 10 seconds then run) sudo /usr/sbin/program

---

### Post by dizee on 2008-05-13
```
sleep 10 && program
``` might work.

---

### Post by linuxed on 2008-05-13
No such luck.  Thanks for the suggestion though.  Basically what I'm trying to accomplish is to make sure that one startup entry loads before another one.  I have two programs setup to autostart when Ubuntu loads.  Unfortunately one of those programs has to start before the other one can load.  If they load out of order then it causes one of the programs to never start at all.  So the problem I'm running into is that they're starting in the wrong order.  I was hoping I could just add a timeout to the startup entry which would allow enough time for the other program to load before trying to load the second one.  Any other ideas?

---

### Post by dizee on 2008-05-14
Well you could write a script. Open a text editor and type
```

#!/bin/bash
sleep 10
program &

```
Save it as script.sh and make it executable (should be in the file properties when you right-click on it, otherwise run "chmod a+x script.sh" in the terminal).

Of course you should probably call it something more meaningful than script.sh - i'll just use that for convenience here.

Now the next trick is to link the script so you can run it like a regular program with one command:
```

sudo ln -s ~/script.sh /usr/local/bin/programscript

```
Replace programscript with whatever command you want to use, so long as it's not already taken. program1 or whatever. 

Then when you add the command ("programscript" in this example) to the autostarted applications it will execute the script, timeout and all. Hopefully anyway. In your case it would be a question of replacing the old program command with this new one in the autostarted apps.

---

### Post by linuxed on 2008-05-15
Perfect!  Problem solved.  Many thanks for your help.  I do have one other question though.  If I were to write a script that would execute both programs one after another would I simply add the additional command on the next line followed by an '&' sign?  What exactly is the '&' sign used for?
```

#!/bin/bash
sudo program1 -s &
sudo program2 -s &

or

#!/bin/bash
sudo program1 -s &
sleep 10
sudo program2 -s &

```

---

### Post by dizee on 2008-05-16
Try it out in a terminal yourself :) Running just the command in a terminal means that if you close the terminal, the program exits as well (usually - there are some exceptions to this). However if you run the command and put the & after it, it runs and returns to the prompt, allowing you to put in the next command (and close the terminal without the program itself exiting as well).

So your example would be correct.

---

