---
title: "procps blues"
date: 2013-10-16
forum: General Help
---

### Post by benpietras on 2013-10-16
Hi, on 12.04 64b.

When I try to update (via a terminal) 

Setting up procps (1:3.2.8-11ubuntu6.1) ...start: Job failed to start

Various googling has yet to fix it..

---

### Post by benpietras on 2013-10-18
Nobody?

installArchives() failed: Setting up procps (1:3.2.8-11ubuntu6.1) ...update-alternatives: warning: forcing reinstallation of alternative /usr/bin/w.procps because link group w is broken.
update-alternatives: warning: not replacing /usr/bin/w with a link.
start: Job failed to start
invoke-rc.d: initscript procps, action "start" failed.
dpkg: error processing procps (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
Errors were encountered while processing:
 procps
Error in function: 
Setting up procps (1:3.2.8-11ubuntu6.1) ...
update-alternatives: warning: forcing reinstallation of alternative /usr/bin/w.procps because link group w is broken.
update-alternatives: warning: not replacing /usr/bin/w with a link.
start: Job failed to start
invoke-rc.d: initscript procps, action "start" failed.
dpkg: error processing procps (--configure):
subprocess installed post-installation script returned error exit status 1

---

### Post by Chris_Keller on 2013-10-18
No answer, but having the same problem on two installations of 12.04.

---

### Post by Chris_Keller on 2013-10-19
see also, for example: [https://bugs.launchpad.net/ubuntu/+source/procps/+bug/1241376](https://bugs.launchpad.net/ubuntu/+source/procps/+bug/1241376)

---

### Post by benpietras on 2013-10-21
Ok, fixed it.

if you run this

cat /etc/sysctl.d/*.conf /etc/sysctl.conf | sudo sysctl -p -

you might see a line
 
kernel.yama.ptrace_scope = 1

to see where this line is linked to

grep kernel.yama.ptrace_scope /etc/sysctl.d/*.conf /etc/sysctl.conf

and then comment it out in /etc/sysctl.d/10-ptrace.conf

Now you can update / upgrade again.

---

### Post by brosskgm on 2013-10-23
After doing above still failed update ubuntu 12.04 64b


installArchives() failed: Setting up procps (1:3.2.8-11ubuntu6.1) ... 
start: Job failed to start 
invoke-rc.d: initscript procps, action "start" failed. 
dpkg: error processing procps (--configure): 
 subprocess installed post-installation script returned error exit status 1 
No apport report written because MaxReports is reached already
Errors were encountered while processing: 
 procps 
Error in function:  
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1) 
Setting up procps (1:3.2.8-11ubuntu6.1) ... 
start: Job failed to start 
invoke-rc.d: initscript procps, action "start" failed. 
dpkg: error processing procps (--configure): 
 subprocess installed post-installation script returned error exit status 1

---

### Post by brosskgm on 2013-10-23
Fixed. I opened /etc/sysctl.d/10-zeropage.conf and changed vm.mmap_min_addr = 65536 to 65535

---

### Post by godfree2 on 2013-10-24
> **brosskgm said:**
> Fixed. I opened /etc/sysctl.d/10-zeropage.conf and changed vm.mmap_min_addr = 65536 to 65535

that did not work for me
neither did the 
/etc/sysctl.d/10-ptrace.conf
procedure

---

### Post by Chris_Keller on 2013-10-26
have you 'see also, for example: [https://bugs.launchpad.net/ubuntu/+s...s/+bug/1241376]("https://bugs.launchpad.net/ubuntu/+source/procps/+bug/1241376")'.
check files for procps in directory upstart for error. In my case just needed to add a new line in one of the .conf's

---

