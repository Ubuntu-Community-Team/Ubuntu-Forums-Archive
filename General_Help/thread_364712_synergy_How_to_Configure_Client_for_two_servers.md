---
title: "synergy How to Configure Client for two servers"
date: 2007-02-18
forum: General Help
---

### Post by sephirothsigep on 2007-02-18
I have 3 computers all together. two of them are servers for the same client. what i want to be able to do is have that client connect to both the servers at the same time. The Client computer is a dual boot XP and linux (ubunut), so i need to be able to set the client up on both sides to accept both servers. 

TVCOMP = client (xp and Linux) 
 
THEGREENMACHINE = server (xp) 
 
LAPTOP (Linux)

---

### Post by airtonix on 2007-03-29
yeah....what you normally expect a synergy client to do.....the synergy server does instead.

the synergy server(source of keyboard and mouse) serves out the controlling keyboard and mouse commands to the listening client(slave) that currently has the focus of the mouse. 

to do this create the config file : 

>  leafpad ~/synergy.conf or with gedit....
>  gedit ~/synergy.conf then dump this in there....
>  
section: screens
 TVCOMP:
 THEGREENMACHINE:
 LAPTOP:
end

section: links
 TVCOMP:
  left=LAPTOP
  right=THEGREENMACHINE
 LAPTOP:
  right=TVCOMP
 THEGREENMACHINE:
  left=TVCOMP
end
now from TVCOMP.....run : 

> synergysthen from LAPTOP & THEGREENMACHINE...... run : 

> synergyc TVCOMPgive it 30secs-1min to kick in.

if nothing happens and your mouse from TVCOMP cany'not enter the screens of either the other two then run the same commands again cept with -f on the end (but before the synergy servers host name)  like so 

From TVCOMP.....run : 

> synergys -fthen from LAPTOP & THEGREENMACHINE...... run : 

> synergyc -f TVCOMPthis will reveal debug info.

---

