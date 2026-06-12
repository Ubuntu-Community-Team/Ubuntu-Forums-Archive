---
title: "delay in pw prompt when ssh'ing into ubuntu"
date: 2007-05-05
forum: General Help
---

### Post by jmartrican on 2007-05-05
This is actually a problem I have encountered on multiple systems across multiple distros and even Solaris.  I ssh into a server and notice a delay in getting a username or password prompt.  Currently I'm having a delay in getting the pw prompt when ssh'ing into my ubuntu server.

Any ideas what this could be?

thanks

---

### Post by asipi on 2007-05-07
could be that ssh server is starting from xinetd or inetd
if you have a dedicated ssh server process the prompt should come up instantly

---

### Post by Titus A Duxass on 2007-05-07
I experience short delays when sshing as well, but it's only 5 - 10 seconds so it's not a problem.

How long is your delay?

---

### Post by jmartrican on 2007-05-08
I think it ranges from 10 - 30 seconds.  SSH is standalone, not in inetd.conf

---

### Post by mccorkle on 2008-01-14
Delays when ssh'ing in are almost always DNS related.  To diagnose this, ssh into the machine from a known good box (that doesn't see the delays elsewhere) with the command line "ssh -vv username@hostname" and see where the delay is.  It's likely that the server that is giving you the delay is trying to reverse lookup the IP of the machine you are sshing from and timing out (hence the delay).  

To fix, edit your ssh config ("/etc/ssh/sshd_config") and add a "UseDNS no" line (or change the existing one to this).  

Then restart your sshd via "sudo /etc/init.d/ssh restart".

Hope that helps.

::Mark McCorkle

---

