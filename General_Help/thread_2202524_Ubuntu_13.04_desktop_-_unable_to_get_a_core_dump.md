---
title: "Ubuntu 13.04 desktop - unable to get a core dump"
date: 2014-01-29
forum: General Help
---

### Post by bd96a3 on 2014-01-29
I'm fighting a problem wherein I'm unable to get a core dump file to be created.  I'm running a 64 bit version of 13.04 desktop.  One thread I ran across talked about the APPORT package and how that can inhibit core dumps.  I have removed that package.  I also updated the /proc/sys/kernel/core_pattern to have this line in it: core.%e.%p.%h.%t.  However, every time I reboot it gets changed back to "core".   Yet, there are NO files on my system anywhere called "core" to correspond with the program crash (SIGSEGV).  This crash should have caused a core dump file to be produced, but it doesn't.  Oh - I also have ulimit set to "unlimited" - confirmed by ulimit -a.  

What have I missed?  

Since the core_pattern file keeps getting reset every time I reboot I know something is still overwriting my value.  What is causing this?  Maybe if I can find out what is doing this I can find out what is preventing core dumps from getting created.

Note:  I did spend a couple of hours searching forums and trying all the different examples given.  I still have not found the solution.

Thanks in advance for any help you can provide.

---

### Post by mörgæs on 2014-01-30
Hi, welcome to the fora.

13.04 is now an abandoned release. If bugs are found they will not be fixed.

Your best option is to begin with a clean install (not upgrade) of 13.10. Please post again if you still have the problem.

---

### Post by bd96a3 on 2014-01-31
Thank you for the reply.  I did not know 13.04 was dead.  However, I have a lot of time and effort invested in getting the application I'm trying to debug running on this machine.  I find it hard to understand that there is nothing else I can look at in order to get a core dump to occur.  Really, have I done EVERYTHING possible?

---

### Post by bd96a3 on 2014-02-03
Anything else I can do to troubleshoot this problem?  Am I on the right track so far?

Thanks for any help.

---

### Post by steeldriver on 2014-02-03
> **bd96a3 said:**
> Yet, there are NO files on my system anywhere called "core" to correspond with the program crash (SIGSEGV).

Do you mean that there *is* a core file, but it is not related to the most recent SIGSEGV (or even to the same executable)? If so you may be experiencing this bug

[https://bugs.launchpad.net/ubuntu/+source/apport/+bug/160999](https://bugs.launchpad.net/ubuntu/+source/apport/+bug/160999) 

I just confirmed it applies on my 12.04 box as well

---

