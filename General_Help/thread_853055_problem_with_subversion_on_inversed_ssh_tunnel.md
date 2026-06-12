---
title: "problem with subversion on inversed ssh tunnel"
date: 2008-07-08
forum: General Help
---

### Post by XoRDy on 2008-07-08
Greetings,

I've got a problem that I'm not able to solve:

I've got 2 servers:
server1 is in our LAN, and it's not accessible from internet.
server2 is an production server.

server2 has to be able to do status, checkouts and commits to server1

To do so, I made an inverse ssh tunnel from user@server01 to root@server02 in port 22222, and in server02 I edited /root/.subversion/config

And in [tunnels], I put this this line:
byussh = ssh -p 22222 -l user

Then I started the tunnel from server01:
[email]user@server01:~/.ssh[/email]# ssh -l root -R 22222:localhost:22 -f -N server02

And then from server02 I made a svn status, and It works:
[root@server02 proyect]# svn ls svn+byussh://localhost/var/svn/proyect/
(with the inverse tunnel I have to connect localhost, this command works well)

But when I made a commit, it doesn't work:
[root@server02 proyect]# svn ci . -m"asdasd"
Adding         testfile
Transmitting file data .svn: Commit failed (details follow):
svn: Can't create directory '/var/svn/proyect/db/transactions/875-1.txn': Permission denied

Then I tried stalishing a tunnel from root@server01, instead from user@server01, and then I can do commits!
If I do a commit from the console with user, it works, but not  when I do it over the inverse tunnel

What's happening? I need to do commits with that user from the tunnel.

PD: I used this tutorial for creating the tunnel: [http://blog.inquirylabs.com/2007/01/20/using-subversion-via-a-2-hop-ssh-tunnel/](http://blog.inquirylabs.com/2007/01/20/using-subversion-via-a-2-hop-ssh-tunnel/)

Thank you

---

