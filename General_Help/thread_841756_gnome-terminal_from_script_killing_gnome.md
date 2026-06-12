---
title: "gnome-terminal from script killing gnome"
date: 2008-06-26
forum: General Help
---

### Post by sjv on 2008-06-26
I have what seems to be a *really* strange problem. I have a bash script that looks like this:

```

#!/bin/bash
DEV_PATH=dev/work/site/trunk
gnome-terminal -t autotest --working-directory=$DEV_PATH --geometry=85x60+1025+100 -x autotest
gnome-terminal -t psql --working-directory=$DEV_PATH --geometry=180x60+1700+100 -x psql site_dev site
gnome-terminal -t log --working-directory=$DEV_PATH --geometry=100x65+2500+85 -x tail -f log/development.log
cd $DEV_PATH

```

Real simple. It's just used to open up some gnome terminals, and change the current directory(it's run as source so the final 'cd' will work) to the main working dir. Sometimes it runs fine, other times one or more of the terms won't open. 

When it happens that one of them doesn't open, I can't open any other nautilus or terminal windows.  This doesn't get fixed until a full reboot happens. Restarting gdm doesn't have any effect. 

This seems really strange given the simplistic nature of what I'm trying to do. Any ideas on what might wrong, or where I could even start looking?

Thanks,
Steve

---

### Post by owlgorithm on 2008-06-26
Perhaps you should use an absolute path instead of dev/work/site/trunk? I feel like that might cause problems if your current directory were /.

---

### Post by sjv on 2008-06-26
Yeah, I changed that, though up to this point I have always run the command from my home dir.

---

### Post by owlgorithm on 2008-06-26
You could try using -e instead of -x to enter exact string commands and also try using explicit flags inside the psql command to make sure it is doing exactly what you intend it to, even if you don't *have* to use them. This could make it easier to debug, at least, because I wouldn't expect everyone knows psql (I sure don't -- I read the man page).

Nice screen, by the way :-)

---

### Post by owlgorithm on 2008-06-26
Try including & at the end of gnome-terminal lines like this:
```

#!/bin/bash
DEV_PATH=dev/work/site/trunk
gnome-terminal -t autotest --working-directory=$DEV_PATH --geometry=85x60+1025+100 -x autotest [COLOR="Blue"]&[/COLOR]
gnome-terminal -t psql --working-directory=$DEV_PATH --geometry=180x60+1700+100 -x psql site_dev site [COLOR="Blue"]&[/COLOR]
gnome-terminal -t log --working-directory=$DEV_PATH --geometry=100x65+2500+85 -x tail -f log/development.log [COLOR="Blue"]&[/COLOR]
cd $DEV_PATH

```
At least in my testing on my Mac (I don't have access to my Ubuntu machine right now) with the following version, the script can't advance to the next xterm unless the previous one has closed unless the commands have been launched as background processes:
```

#!/bin/bash

DEV_PATH=~/
xterm -geometry 80x24+0+0 -e top &
xterm -geometry 80x24+0+0 -e python &
xterm -geometry 80x24+0+0 -e tail -f $DEV_PATH/foo.txt &
cd $DEV_PATH

```

Failing that, you might check these, because they seem related.
[https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/221144]("https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/221144")
[https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/191107]("https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/191107")

---

### Post by owlgorithm on 2008-06-26
I think this is the same problem:
[http://georgia.ubuntuforums.org/showthread.php?p=5270267](http://georgia.ubuntuforums.org/showthread.php?p=5270267)

Unfortunately it doesn't have a solution yet either. I wonder, from some of the above links, if this is caused by a bug in gnome-terminal related to the --geometry argument.

---

