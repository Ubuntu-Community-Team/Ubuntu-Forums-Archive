---
title: "Accidently deleted PATH variable, what now?"
date: 2008-01-17
forum: General Help
---

### Post by punzak on 2008-01-17
Its hard to know where to start on this one.  I was trying to update the path variable to include another file to cure an error I was getting, now I can't do anything in the terminal without getting all kinds of errors.

when I run gedit, I get:

```
Command 'gedit' is available in '/usr/bin/gedit'
The command could not be located because '/usr/bin' is not included in the PATH environment variable.
bash: gedit: command not found
```

when I try to run /usr/bin/sudo su, in an effort to fix bash.bashrc I get this:

```
me@computer:~$ /usr/bin/sudo su
[sudo] password for me:
bash: lesspipe: command not found
bash: Command: command not found
bash: The: command not found
bash: dircolors: command not found
bash: Command: command not found
bash: The: command not found
```

Anyone got any great ideas?  Or am I screwed?

---

### Post by bodhi.zazen on 2008-01-17
How did you delete $PATH ?

Unless you edited a system file of ~/.bashrc you can just close your current terminal and open a new one.

Or in a console, log off and back on.

For sudo, use 

sudo -i

(rather the sudo su)

---

### Post by punzak on 2008-01-17
RE: How?

Answer:
export PATH=$UNDEFINED: /path/to/something

I did however realize that even though I got all those errors with sudo su, it did grant me root.  So I was able to fix the file.  Thx for the quick response!

---

### Post by bodhi.zazen on 2008-01-17
OK, that command is temporary, ie your path will be re-set when you start a new shell.

If you want to make the changes permanent , you need to edit ~/.bashrc

Add 

PATH=$PATH:/path/to/something
export $PATH

---

