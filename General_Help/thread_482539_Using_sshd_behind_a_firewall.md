---
title: "Using sshd behind a firewall"
date: 2007-06-23
forum: General Help
---

### Post by bfawlty on 2007-06-23
Hello all:

I'm trying to connect to my home computer with ssh.  I have installed & configured openssh-server and ssh localhost works fine.  But I can't access my machine from a remote server -- ssh my-ip-address pauses and then times out.  I initially assumed this meant I'm behind a firewall, but I tried  changing the sshd port setting and none of the standard ones (22, 80, 443) or other random ones works -- ssh -p XXX my-ip-address also times out.  I don't know what to make of this behavior.

So I have two questions: 
1. Is it plausible that this is due to a firewall?
2. How do I test that theory?  (Or any other theory you have.)

Thanks!

---

### Post by schallstrom on 2007-06-23
Hi bfawlty,
What exactly is 'remotely'? Are you trying to connect from the same network or is there a router/firewall in between? If so, it could well be that the router is blocking the ssh traffic. 
If you have a router, can you configure the packet filter mechanism on it? Do you have administrative access to it? Check it to allow ssh traffic (TCP port 22) and maybe you have to configure a NAT.
You could also run a tcpdump on the machine running the sshd and try to connect. If you see packages for port 22 with a source IP of the machine you are connecting from the problem is probably caused by the machine running the sshd itself, not by a router or firewall.
If you give me some more precise information, maybe I am able to help you.

---

