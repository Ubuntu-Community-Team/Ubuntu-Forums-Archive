---
title: "Can't su in failsafe terminal"
date: 2006-11-14
forum: General Help
---

### Post by gedion_ki on 2006-11-14
Ok I am pretty sure I know what I did to get myself in this situation but I cant seem to fix it! 

First my problem: I changed something on a config (I'll explain that in a sec) and now I can only start a failsafe terminal session. For some reason when I log in with my user account I can't su to root so I can go fix my problem. It tells me that the "command is unavailable". Well I can't fix my mess with out being root so I'm pretty much stuck. Oh the ls command is also unavailable which doesn't help me much as I'm a bit of a Linux noobie. How can I run su and perhaps even ls so I can find the file I changed and fix it?

I tried to run it by going to the sbin dir but su isn't located there I guess.

Help?


If your wondering how I managed this feat, I was attempting to add Sun Java to the path and to JAVA_HOME, well the info I found on the net told me to ad the lines in the etc/environment file (I think maybe it was suppose to be in a directory instead) but I added it there and rebooted and now I'm stuck here. Any additional advice on how to get Java installed correctly would be appreciated as well.

Thanks for reading!

---

### Post by aidanr on 2006-11-14
you must have messed up the "PATH" string in /etc/environment somehow

this is what mine looks like
```
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games"
LANG="en_US.UTF-8"
```

does "sudo su" work?
if all else fails, boot up the live cd, mount your / partition and fix the file from the live cd

---

### Post by CatKiller on 2006-11-15
> **gedion_ki said:**
> I tried to run it by going to the sbin dir but su isn't located there I guess.

```
iain@weatherwax:~$ which su
/bin/su

```

---

### Post by gedion_ki on 2006-11-15
Thanks for the quick response guys! That did it, I couldn't sudo either as I had totally killed the path settings. So I went to ./bin and ran ./su root from there. After that it was simply getting the path right to run nano correct my little path mess up.

It was big mistake, but a great learning experience so it was well worth it. Thanks again for the help!

---

