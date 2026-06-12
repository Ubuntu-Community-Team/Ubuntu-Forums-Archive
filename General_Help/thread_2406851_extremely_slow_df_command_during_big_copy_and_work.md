---
title: "extremely slow df command during big copy and work around"
date: 2018-11-26
forum: General Help
---

### Post by Skaperen on 2018-11-26
while doing a big copy (nearly a TB) from one disk to another, i notice that while my system was generally a tad bit sluggish, the [FONT=courier new]df[/FONT] command was extremely slow, in worst case taking 100 seconds to complete, and always at least 50 seconds. so out of curiosity which syscall(s) might be lagging, i ran it under [FONT=courier new]strace[/FONT].  then it ran fast no matter what.  so i made a temporary shell function to run it under strace ... [FONT=courier new]_df() { strace -o /dev/null /bin/df "$@"; }_[/FONT] to work around the problem for a while.  then typing in [FONT=courier new]df[/FONT] under this instance of [FONT=courier new]bash[/FONT] ran about as fast as other commands.

1,  anyone know why df would be especially slow in this case?  i was suspecting it was doing somsync call.

2.  anyone know why strace/ptrace made it run with less time?

---

### Post by HermanAB on 2018-11-26
You can ionice the copy process, then the rest of the system will become responsive again.

---

### Post by Skaperen on 2018-11-26
actually, the rest of the system does not get any better when i run the copy under ionice.  the reason for that is because the slowdown is not the result of i/o contention.  instead, it is memory flushing.  the copy floods outbound memory buffers, which causes thing like the shell, the terminal window. and the x server, to me swapped out.  to run the command, all of these need to be swapped back in and that takes time.  [FONT=courier new]ionice[/FONT] can improve it somewhat by not contending with those swap operations.  what can improve this is to confine the copy to a finite fraction of buffer space.  this is doable with containers an running the copy in its own container.

---

