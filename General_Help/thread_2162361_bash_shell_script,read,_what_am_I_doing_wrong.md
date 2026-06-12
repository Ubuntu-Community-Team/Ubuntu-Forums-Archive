---
title: "bash shell script,read, what am I doing wrong ?"
date: 2013-07-14
forum: General Help
---

### Post by Lewis Balentine on 2013-07-14
this is the line from the script
read -N 1 -t 10 -p press any key

I am running Ubuntu 12.04 LTS (X32) with gnome-fallback
shell is GNU bash, version 4.2.25.
If I enter "read --?" at the prompt it responds:
  read: usage: read [-ers] [-a array] [-d delim] [-i text] [-n nchars] [-N nchars] [-p prompt] [-t timeout] [-u fd] [name ...]

The line in the script is:  
read -n 1

bash responds "illegal read option -n"

all I really want is a simple "pause".
dead simple in MS-DOS. 
Seems extremely challenging in linux.

=================================
my answer:
I am not putting #!/bin/bash to specify the shell.

---

### Post by prodigy_ on 2013-07-14
> **Lewis Balentine said:**
> 
The line in the script is:  
read -n 1

bash responds "illegal read option -n"
I could not reproduce this in bash 4.2.25.

---

### Post by Lewis Balentine on 2013-07-14
apparently I was not getting bash but something else.
I added #!/bin/bash as the first line ....

now my question is what does gnome use for a shell program or have I screwed that up somehow?

---

### Post by efflandt on 2013-07-14
Ubuntu uses **dash** for default sh non-interactive shell (read: man dash) due to less overhead. If you need a script to do something bash specific, you need to include the path to **bash** instead of **sh**.

---

### Post by Lewis Balentine on 2013-07-14
that explains it ...
thank thee

---

