---
title: "command line short cuts"
date: 2007-09-02
forum: General Help
---

### Post by fearevilleet on 2007-09-02
Hi,

Is there a way to create a terminal shortcut for use in the command line? For example I have to type sudo stunnel4 /etc/stunnel/snntp.conf every time I want to start stunnel and other programs. Anyway I could make a shortcut so I can just type in stunnelstart so something else of my choosing to run the command?


Thanks!

---

### Post by csimons on 2007-09-02
You can you 'alias' to set command shortcuts in bash (and probably other shells).

For example, the following will execute 'ls -al' every time you enter 'dir':

alias dir='ls -al'

Putting these aliases in your .bashrc or .bash_profile will ensure they're automatically available whenever you're in the shell (assuming you use bash, which is the default shell in Ubuntu).

---

### Post by fearevilleet on 2007-09-02
Thanks, that seemed to work.

So should I add 

alias startstunnel="sudo stunnel4 /etc/stunnel/snntp.conf"

to my .bash_profile to save it or is running the command enough?

---

### Post by csimons on 2007-09-02
Running the command will be enough to keep the alias for your current session, but as soon as you close the shell it will be lost.  Putting it in .bash_profile or .bashrc will load it each time you open a new shell session.

---

