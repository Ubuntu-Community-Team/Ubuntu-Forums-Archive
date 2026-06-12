---
title: "Need help with SSH...thanks in advance"
date: 2007-09-15
forum: General Help
---

### Post by punkybouy on 2007-09-15
Does anyone have any idea why I cannot use the "Places/Connect to server" method of connecting from one 6.06 LTS machine to another yet I can from the command line?  I am using SSH both ways and connecting at the command line (ssh me@theothermachine ) works like a breeze.  When I try to set up a connection via Places/Connect to Server and set up SSH there with the same connection info I get prompted for a password from the remote machine but I never get in.

---

### Post by rivalarrival on 2007-09-15
It looks like you're doing two different things...

"ssh me@theothermachine" doesn't mount the remote filesystem to your local machine, it just gives you a terminal window from the remote machine on your local machine.

connecting to the server (places > connect to server...) with SSH tries to mount the remote file system in a folder (mount point) on the local file system, giving you access to   the files on the remote machine.

I would suggest that you follow the instructions here:
[http://ubuntu.wordpress.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/](http://ubuntu.wordpress.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/)

It will either work this way, or it will at least give you some more meaningful errors.

---

