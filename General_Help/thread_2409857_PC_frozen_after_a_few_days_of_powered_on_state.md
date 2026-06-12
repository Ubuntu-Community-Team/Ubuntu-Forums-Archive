---
title: "PC frozen after a few days of powered on state"
date: 2019-01-07
forum: General Help
---

### Post by onus34 on 2019-01-07
okay so I have a relatively new install of Ubuntu MATE 18.04.1 LTS x64 running Linux Kernel 4.15.0-43-generic x86-64 with Mate 1.20.1

And it has been running fine until about a month ago. 
It's my main work machine, and I leave it running because I work in two buildings and sometimes I need to remote in. 
Well that is no longer helpful, because I'll leave and try to remote in only to find its not available and come back to my office to see it is all frozen up. 
monitors will not power on, no light on the mouse. keyboard completely unresponsive.
If i reboot it is fine and everything works great!
but if I leave it on and alone. boom. its gone again. this has happened 3 times in the span of a few weeks and I do not even know where to start to troubleshoot this issue.

any and all help appreciated. 

thanks!
-onus34

---

### Post by him610 on 2019-01-07
Sounds like a memory leak to me, or possibly overheating. You probably have a couple of alternatives that come to mind. (1) there may be a program running that consumes memory and does not release it. Identify the program, and if not necessary, don't run it. (2) Determine how many days or hours it takes the machine to non-respond then reboot before the time elapses.

Use *top* or *htop *to monitor cpu and memory.

Someone else may chime in with a better better, more practical solution.

---

### Post by Autodave on 2019-01-07
+1 with him610.  Could also be a power supply problem.  And that could also be due to overheating.  I would do what was suggested above, but in the interim, I would remove the side panel from the machine to let more cooling air in.  Are fans clean and functioning?  CPU cooler clean?

---

