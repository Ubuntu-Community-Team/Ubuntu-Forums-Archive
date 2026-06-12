---
title: "Monitor shell scripts being run"
date: 2008-07-10
forum: General Help
---

### Post by jonlemur on 2008-07-10
Is there a way that I can monitor what shell scripts are being called by all programs?  For instance, I have a device that receives IR commands from a controller.  Then it executes some shell scripts.  But I have no idea what is being executed, or how to find out.  Any ideas, or do I need to give more information?

Thanks

---

### Post by HalPomeranz on 2008-07-10
You can monitor a single process with strace:

```

$ **ps -ef | grep inetd**
hal       2366  7371  0 07:11 pts/1    00:00:00 grep inetd
root      5867     1  0 Jul05 ?        00:00:00 /usr/sbin/xinetd -pidfile /var/run/xinetd.pid -stayalive
$ **sudo strace -f -p 5867 >/tmp/OUTPUT 2>&1 &**
[1] 2468
$ **tail -f /tmp/OUTPUT | grep exec**
[pid  2505] execve("/usr/sbin/vmware-authd", ["vmware-authd"], [/* 13 vars */]) = 0
   *[... monitor process as long as you want, hit Crtl-C when done ...]*
**^C**
$ **sudo kill 2468**
$
[1]+  Done                    sudo strace -f -p 5867 > /tmp/OUTPUT 2>&1 

```

Note that we use the ps command to figure out the process ID of the process we want to track with strace.  Here I'm tracking the xinetd process which has process ID 5867 ("-p 5867" on the strace command line).  You would want to strace whatever monitor program is firing off all the shell scripts.

strace will track the process ID that you specify and produces a ton of output.  In this case, though, all you care about are the exec*() calls which are used to start other programs.  So we shove the strace output into a file and just grep for the exec calls.  In the example above, xinetd is running the "/usr/sbin/vmware-authd" program.  When you're tired of watching what's going on, just hit Ctrl-C to kill the tail program and return to the shell.

You can leave the strace program running if you want to capture data for a long time, or you can kill it by process ID as we do above.  Note that the process ID is output when we originally started the strace job (see the output line "[1] 2468" after the strace command?), but you can also find it via "ps -ef | grep strace".

---

### Post by jonlemur on 2008-07-10
Thanks, that looks like just what I need.

---

