---
title: "Bash script that toggles a terminal"
date: 2015-10-24
forum: General Help
---

### Post by pterpan on 2015-10-24
Hey.

So I want to map my Caps Lock to a script which would launch a terminal if there isn't any terminal open, and close all terminals if open.

I figure it would look something like this:

```

#!/bin/bash
var1=$(echo | ps ax | grep -v grep | grep bash)
if $var1 = *"bash"*
then
    pkill bash
else
    gnome-terminal
fi

```

But I'm new to coding in bash, and I've been sitting with this for quite some time now.  When run in the terminal, I get the error message

```
./terminal.sh: line 3: 7581: command not found
``` where 7581 is the PID of my terminal.

The program then enters the [FONT=courier new]else[/FONT] statement and terminates.

I've got no clue how to continue with this, so any help would be appreciated!

Cheers.

---

### Post by ajgreeny on 2015-10-24
You can do it more easily with a complex command linked to the key you want, but if you use caps-lock when typing this will not be the one to use.
Try command ```
bash -c "if pgrep gnome-terminal; then killall gnome-terminal; else gnome-terminal; fi"
```
This assumes you are using gnome-terminal; if not change that part of the command to whatever you are using.

---

### Post by pterpan on 2015-10-25
Works like a charm, thanks!!

---

### Post by pterpan on 2015-10-25
Side question. Is it possible to make it kill only the gnome-terminal that was launched with Caps Lock, and not other instances of gnome-terminal?

---

### Post by Lars Noodén on 2015-10-26
> **pterpan said:**
> Side question. Is it possible to make it kill only the gnome-terminal that was launched with Caps Lock, and not other instances of gnome-terminal?

Ubuntu looks like it runs a single instance of [gnome-terminal](http://manpages.ubuntu.com/manpages/trusty/en/man1/gnome-terminal.1.html) with multiple windows, regardless of how the terminals are launched.  I don't see a way to tell it to kill a specific window or tab.  

But then on the other hand the instance of bash/tmux/screen running in the terminal will have a unique process ID.  Perhaps that can be tracked somehow.  Then if that is killed, the parent window or tab will get closed.

---

### Post by Lars Noodén on 2015-10-26
One possible way to toggle a terminal would be something like this:

```

if [ -s /tmp/gtPID ] ;

then
 kill $(cat /tmp/gtPID); 
 rm /tmp/gtPID; 

else
 gnome-terminal -e '/bin/sh -c "echo $$ > /tmp/gtPID; /bin/bash; /bin/rm/gtPID; "'; 

fi

```

It works by having gnome-terminal launch sh (dash) to do two things.  First, it prints its own process id to a file.  Second, it runs bash as a child.  So when sh gets killed, so does the bash that it is running.  

The usual caveats regarding use of PID files apply.

Edit: here's a cleaned up version of that:

```

#!/bin/sh

PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin;

# file name to contain PID and act as flag for toggle
pidfile="/tmp/gtPID";

# tidy up, if necessary
if [ -s "$pidfile" ] && ! ps --no-headers $(cat "$pidfile") >/dev/null; then
        # remove PID file if there is no corresponding process
        rm "$pidfile";
fi

# check PID file flag for toggling
if [ -s "$pidfile" ] ; then
        # read PID file kill corresponding process, then remove file
        kill $(cat "$pidfile");
        rm "$pidfile";
else
        # create PID file while launching a new terminal window with bash
        gnome-terminal -e "/bin/sh -c \"echo \$$ > \"$pidfile\"; /bin/bash;\"";
fi

```

---

