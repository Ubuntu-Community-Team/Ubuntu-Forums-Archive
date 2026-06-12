---
title: "FTP server problem through router..."
date: 2008-05-13
forum: General Help
---

### Post by tenchi39 on 2008-05-13
Hi!

I installed the proftpd server package on my work machine with its's default settings. It works ok on the local network. I have a router and on it in the UPnP Forwarding settings I enabled the ftp entry and seti it to my IP.

Connecting from home works in windows with total commander flawlessly, but in linux (using dolphin and kftpgrabber) it just does not work. It asks for username and password but dies after.

I also tried connecting from the work machine to itself but through the internet using the router's external IP. That didn't work either.

Why only total commander works?

Please help!

---

### Post by DrCoolSanta on 2008-05-13
Let me make somethings clear here.
Most routers can't connect to themselves using their external IP. I can confirm this, because the one my ISP gave couldn't do so, but I got a new router later, which could.
If you want to connect to the machine from outside the internal network of the router, port forwarding should be enabled, and should point it to your machines internal ip address. (It seems you have done this.)
If you want to connect from outside the network, you must use the external ip address but otherwise you should use internal.

If you can't access the server from inside the network, then try pinging to the machine, if it pings then either you are using wrong configuration or there is a problem in the client.

---

### Post by tenchi39 on 2008-05-13
I'm able to connect from the external network to the work machine, but only with total commander in windows. No problems there. The problem is that I cannot connect using dolphin or kftpgrabber...

(Of course I'm using the external IP)

---

