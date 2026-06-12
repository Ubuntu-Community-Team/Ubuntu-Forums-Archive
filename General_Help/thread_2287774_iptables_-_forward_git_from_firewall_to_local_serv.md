---
title: "iptables - forward git from firewall to local server"
date: 2015-07-22
forum: General Help
---

### Post by Drenriza on 2015-07-22
Hi all

I got a raspberry pi 2 that i use as my firewall (eth0 in, eth1 out) between my ISP's supplied box and my internal network.

Behind my firewall i have a server that i am using as a git repository server, that i would like to be able to reach from the outside world.
I have looked at making a ssh tunnel to do this but i am not quite sure that i get it.

As i understand a ssh tunnel, its a encrypted socket connection working in the background that you can send data over, but you don't actual log in over it to the remote machine.

I have tried
```

ssh -L source-port:git.server.behind.firewall:destination-port username@firewall

```

[LIST]
[*]Source port can be any made up port, from the free to use port list. Which functions as my source port.
[*]git.server.behind.firewall is my git servers ip address on my home local network.
[*]Destination port is my ssh service running on the firewall, that i want to use to tunnel through the firewall to the git server.
[*]username is my username on my firewall machine
[*]firewall is the ip address of my ISP box that forwards port 22 to my firewall on my local network.
[/LIST]

but it does not create a (from what i can see) tunnel behind the scene that i can transmit data over, instead it is logging me into the firewall itself.

Am i way way off?

---

### Post by dino99 on 2015-07-22
The most recent howtos:

[http://www.cyberciti.biz/faq/set-up-ssh-tunneling-on-a-linux-unix-bsd-server-to-bypass-nat/](http://www.cyberciti.biz/faq/set-up-ssh-tunneling-on-a-linux-unix-bsd-server-to-bypass-nat/)
[https://help.ubuntu.com/community/SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)
[http://askubuntu.com/questions/636018/how-do-i-set-up-an-encrypted-ssh-tunnel-for-vnc](http://askubuntu.com/questions/636018/how-do-i-set-up-an-encrypted-ssh-tunnel-for-vnc)
[http://www.liquidweb.com/kb/how-to-configure-a-vnc-server-to-use-an-ssh-tunnel-on-ubuntu-14-04-lts/](http://www.liquidweb.com/kb/how-to-configure-a-vnc-server-to-use-an-ssh-tunnel-on-ubuntu-14-04-lts/)

---

