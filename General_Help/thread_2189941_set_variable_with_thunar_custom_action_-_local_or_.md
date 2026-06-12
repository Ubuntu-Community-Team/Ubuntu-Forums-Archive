---
title: "set variable with thunar custom action - local or global"
date: 2013-11-24
forum: General Help
---

### Post by Dreamer Fithp Apprentice on 2013-11-24
My immediate objective would be most elegantly solved by using a thunar custom action to set a variable in the lxterminal running the script that opened thunar. I tried all the obvious things. I THINK it may simply be something thunar just can't do. Please enlighten me if you believe otherwise.

So I decided if I can't do that the next best thing would be to use thunar to set a "global" environment variable. I put global in quotes because I'm beginning to wonder if I misunderstand the concept. I'm seeing tons of how-tos that SEEM to be saying I can use "export" to do this. But with 2 terminals open simultaneously, alternating commands on terminals 1 & 2:
lxterminal 1:```
me@ubuntu:~$ VAR_SPE_TEMP=woe
me@ubuntu:~$ echo "$VAR_SPE_TEMP"
woe
me@ubuntu:~$ export VAR_SPE_TEMP
me@ubuntu:~$ export VAR_SPE_TEMP=duh
me@ubuntu:~$ echo "$VAR_SPE_TEMP"
duh
me@ubuntu:~$ 
```

lxterminal 2:```
me@ubuntu:~$ echo "$VAR_SPE_TEMP"

me@ubuntu:~$ echo "$VAR_SPE_TEMP"

me@ubuntu:~$ echo "$VAR_SPE_TEMP"

me@ubuntu:~$ 
```

What I'm trying to show is that I tried 2 different formulas widely published on the internet for establishing "global" variables in one lxterminal but the other lxterminal doesn't see them. They seem to me to be plain old ordinary stay-at-home variables. What is it about "global" I'm not getting?

I'll summarize:

My immediate goal is to use a thunar custom action to send a variable (path/filename) back to the script I called thunar with.

If I can't do that I want to use a custom action to create a variable that persists after thunar is closed. It doesn't have to persist through log out. It would be better if it didn't.

In any case, just to establish to myself I haven't lost ALL of my marbles can anyone tell me what I'm misunderstanding about "global" variables?

BTW, I've done all this on both a Precise and a Saucy system. 32 bit, openbox only, no other DE in both cases.

-------------------
Added by edit later:
I've thought of a pragmatic kludge: A thunar special action can echo the desired string to a file and the script can set the variable from the contents of the file. So I'm not desperate. Still the questions stand though because
1. The kludge is inelegant with 2 unecessary (in principle) disk operations.
2. I really would like to understand why "export" and global variables don't work hte way I expected them to.

---

