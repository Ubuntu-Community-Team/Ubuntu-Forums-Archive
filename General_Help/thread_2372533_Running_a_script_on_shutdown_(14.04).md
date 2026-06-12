---
title: "Running a script on shutdown (14.04)"
date: 2017-09-26
forum: General Help
---

### Post by jrglez on 2017-09-26
Hello, 
I have read a few posts about how to do this, but it's still not working for me. 
I am trying to run a simple script on shutdown. I only want to use this so grive syncs my google drive before I turn the computer off (I have tested the code and it works).
```
#!/bin/bash

cd ~/grive
grive > ~/Documents/out_grive.txt 2>&1
```

This is what I have tried so far:
[LIST]
[*]Created the script and put it in /etc/init.d
[*]Changed it permissions to make it executable for all
[*]Created a link in rc6.d (I also tried in rc0.d): '$ sudo ln -s /etc/init.d/sync_drive.sh /etc/rc6.d/K99sync_drive.sh' (I also tried naming it K01sync_drive.sh and placing the script directly in rc6.d)
[/LIST]
Am I missing something?

---

### Post by TheFu on 2017-09-26
Yes, you are missing many things.

1) The script assumes YOUR userid.  Linux is multi-user.  System-wide startup and shutdown scripts run as root, not your userid.
2) The script assumes YOUR environment.  System-wide scripts have a minimal environment with a very small PATH.
3) ~/ doesn't work in a script like this. $HOME isn't set.

The fixes are:
a) Use fully specified programs.  Never trust the PATH.
b) HOME is not set.  Use fully specified paths for the output file.
c) Force the script to run with your userid.  That means using **su - ** to run the grive command. Something like:
```
#!/bin/sh

TOP_DIR=/home/---put-your-userid-here
PRG=$TOP_DIR/bin/--put-name-of-script-file-here
RUNAS_USER=--put-your-userid-here

cd $TOP_DIR

case $1 in
start)
        su - $RUNAS_USER -c "$PRG start" &
        ;;
stop)
        su - $RUNAS_USER -c "$PRG stop" &
        ;;
restart|reload|force-reload)
        su - $RUNAS_USER -c "$PRG restart" &
        ;;
status)
        echo "Not implemented"
        ;;
*)

```
    
d) The redirection seems wrong to me.
e) The script needs to handled start/stop/restart/status options.  These are normal for all init.d/ scripts. You can look at the others in that directory for more examples.
f) I don't know what grive is (I don't use public cloud storage), but seems like different start and stop options would be necessary.  If grive is a GUI, it won't work.

BTW, the *cd ~/grive*  line is probably worthless.  It might matter, if the command cares about the `pwd`.

---

