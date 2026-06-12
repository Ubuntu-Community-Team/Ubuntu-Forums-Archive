---
title: "Where to set system PATH?"
date: 2004-11-01
forum: General Help
---

### Post by Bob Collins on 2004-11-01
I got an answer as to where to set system environment variables yesterday and got a quick answer...put them in the /etc/environment
file (instead of /etc/profile, which is ignored). 

This works fine for _new_ environment variables but does not work for the PATH variable where you want to append. In fact, trying to append to the PATH in the /etc/environment file appear to replace PATH which hoses starting up a new session from the gdm.

So...where do I append to the system PATH variable?


Additional Info:
I had asked where /etc/environment was sourced from and I know at least it is sourced each time you enter the gdm, ether from startup or logging out of a session. Also, it is sourced before /etc/gdm/Xsession is sourced.

Thanks,

Bob Collins
Sunnyvale CA USA

---

### Post by Bob Collins on 2004-11-02
Bump

---

### Post by mercurus on 2004-11-03
[QUOTE=Bob Collins]Bump[/QUOTE]
 You can always override the system path using the ~/.bash_profile file, but that is a per user solution and not a system-wide solution.

gdm also appears to set path variables in /etc/gdm/gdm.conf, but the comments suggest that "profile scripts" will likely override that configuration.

Are you appending the $PATH variable by referencing it ?
eg. PATH=$PATH:/home/mercurus/bin
Try putting something like that in /etc/environment or /etc/profile

Cheers
mercurus

---

### Post by Bob Collins on 2004-11-03
Hi Mercurus,
Actually ~/.bashrc is the one that will work on a per user basis. /etc/profile and ~/.bash_profile are only read when launching a shell from login and not from within an X session. You can simulate login by running "bash -login".

I did more testing on /etc/environment and $PATH is not "visable" when /etc/environment is being sourced so appending assignment does not work.

So, I still don't have the answer.

Thanks,

Bob Collins

---

### Post by Bob Collins on 2004-11-03
Hi all,
While I was writting the last message, I had another idea and found the answer. The correct place to add system environment variables including PATH is the /etc/bash.bashrc file. Although you can add some variables to the /etc/environment file, I see no reason to do so.

Cheers,

Bob Collins
Sunnyvale CA USA

---

