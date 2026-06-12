---
title: "SSH/rdesktop - cannot connect to SSHD server"
date: 2013-04-23
forum: General Help
---

### Post by RaHorakhty on 2013-04-23
My Ubuntu won't allow SSH connections to the SSH serveron my BT5R2.   Putty closes the connections and displays a "Connection reset by peer"  err msg.  Nmap 192.168.x.x shows that SSHD is active and running on the  remote machine, port 22.  The cmdline of SSH version doesn't work  either.

The [instructions]("http://klinkner.net/%7Esrk/techTips/ssh-remote/") I followed are [confusing!]("http://inside.mines.edu/%7Egmurray/HowTo/sshNotes.html")  Can somone explain how to set up a secure SSHD daemon on BT5R2, step by step.  The [guides]("http://realprogrammers.com/how_to/set_up_an_ssh_tunnel_with_putty.html") recommend using puttygen for the pub key and then saving it to a file, some recommend using openssh.  

I can't figure the conf file and pub/private keys.  I got vsftp up and  running on port 21. Now I want to use rdesktop through a ssh tunnel.

---

