---
title: "ie4linux only starts once until reboot."
date: 2008-05-12
forum: General Help
---

### Post by ade234uk on 2008-05-12
When I reboot Ubuntu I can open IE6 using ie4linux. If I close IE6 I cannot re-open it again until I do a complete reboot. 

Anyone else experienced this problem?

---

### Post by zenwalker on 2008-05-12
Tried launching from cmd line? What error u get?

---

### Post by ade234uk on 2008-05-12
When I run it from the command line, there is about a 14 second delay. There are no errors appearing on the command line. So the next question is, how do I stop the delay lol?

---

### Post by skymera on 2008-05-12
> **ade234uk said:**
> When I run it from the command line, there is about a 14 second delay. There are no errors appearing on the command line. So the next question is, how do I stop the delay lol?

Maybe it is running in the background?

How about trying to kill the process.
If thats the case we need to find out why its running in background :???:

---

### Post by kikke on 2008-05-12
Confirmed, same happens with my IEs4Linux. And the ie7 version doesn't works (I know, it's beta). Newer version of wine from wine's repo doesn't resolve the problem. So I use VirtualBox with rdesktop for ie7 and other windows-based programs.

I haven't got IEs4Linux now, but you can try to killall wine-server before starting ~/.bin/ie6. It's not very safe because it's kill all wine session. Maybe the solution is creating a PID-file with running ie6's pid as content and next start only kill that. But how can we disable the killing method if we want to run two ie6 instances? Wine can give information about processes? Anybody knows about it?

---

