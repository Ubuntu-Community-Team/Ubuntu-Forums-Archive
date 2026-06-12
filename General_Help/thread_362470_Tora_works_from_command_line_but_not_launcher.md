---
title: "Tora works from command line but not launcher"
date: 2007-02-15
forum: General Help
---

### Post by David Mulligan on 2007-02-15
I've compiled Tora from source as the copy available via apt-get does not support oracle.  The good news is that it works great from the command line but the bad news is that it does not work from the launcher.  With or without a terminal it appears to open but I never see Tora and it closes immediately.  I've found no indications as to what is wrong.

I've also preceded the command with gnome-terminal with and without -e.

How can I get output from the launcher?   I've tried piping the output from the tora executable to a file in my home directory with no luck.

Thanks,
David

---

### Post by David Mulligan on 2007-02-20
No ideas?

---

### Post by Maestro23 on 2007-02-20
.

---

### Post by KeighleHawk on 2007-03-19
So has no one figured this one out yet?  I swear it worked for me when I first set it up, but perhaps I was imagining that because today, it does not work....

---

### Post by KeighleHawk on 2007-03-19
okay, FWIW, I created a small shell script with my Oracle related environment variables and then called tora (in the script), then set the launcher to run the shell script.  Still, it seems a more elegant solution should be available...?

...start script...

export ORACLE_BASE=/oracle
export ORACLE_HOME=/oracle/10g_client
export ORACLE_SID=orcl10
export LD_LIBRARY_PATH=$ORACLE_HOME/lib
export PATH=$PATH:$ORACLE_HOME/bin

/usr/local/tora/bin/tora

...end script...

---

### Post by David Mulligan on 2007-04-30
Awesome!  I now have it running from a script too thanks to you.  I have it down to the following though:

ORACLE_HOME=/usr/lib/oracle/xe/app/oracle/product/10.2.0/server
LD_LIBRARY_PATH=$ORACLE_HOME/lib: $LD_LIBRARY_PATH

export ORACLE_HOME ORACLE_SID=XE LD_LIBRARY_PATH

/usr/local/tora/bin/tora

Thanks!
David

---

