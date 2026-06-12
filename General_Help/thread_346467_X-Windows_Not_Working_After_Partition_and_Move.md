---
title: "X-Windows Not Working After Partition and Move"
date: 2007-01-25
forum: General Help
---

### Post by bbjonz on 2007-01-25
Hi Everyone,

I did some moving and shaking on my Dapper Drake server yesterday.  All worked well until I rebooted, and now I can't get X-Windows to work over SSH.  All I did was repartition my hard drive and put /var and /tmp on a separate partition.  Read somewhere that that was a smart thing to do.  After the reboot, though, I get "cannot open display".  After hours of searching, I found a tip that said to try restarting the X-server with "startx."  Here's the output:

X: cannot stat /etc/X11/X (No such file or directory), aborting.

Did I goof something up with moving /var to another partition?  That's the only thing I can think of.  Firewalling shouldn't be an issue because it's SSH (and that's open) and I did use -X when logging in.  Any help is appreciated.

Just to be clear, I'm trying to log in remotely using ssh -X username@server.  I'm not trying to run X-windows on the actual machine.

More troubleshooting: I can log into my university account and run x programs  (e.g, xclock) just fine.  When I use the same machine (my powerbook) to login to my Ubuntu box, it doesn't work.  Importantly, it doesn't forward the display--the DISPLAY variable is empty.  Not so when I login to the university machine.  Using ssh -X...



Joe

---

