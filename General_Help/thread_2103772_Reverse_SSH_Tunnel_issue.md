---
title: "Reverse SSH Tunnel issue"
date: 2013-01-11
forum: General Help
---

### Post by fkasmani on 2013-01-11
Hello,

I'm working on setting up an unattended Ubuntu PC with Ubuntu Server 12.04 and since this PC will be placed in a remote location with no keyboard or screen (unattended), I need to have a permanent SSH connection from this machine to a middle-server (between itself and me) - reason being, this PC will be behind a NAT firewall.

I followed dot-to-dot instructions at 
[http://wiki.fabelier.org/index.php?title=Permanent_Reverse_SSH_Tunneling](http://wiki.fabelier.org/index.php?title=Permanent_Reverse_SSH_Tunneling)
but when I connect, I just get an error> ssh: connect to host 5.175.145.251 port 19999: Connection refusedSo I went back googling for a solution and found
[http://www.alexonlinux.com/reverse-ssh-tunnel-or-connecting-to-computer-behind-nat-router](http://www.alexonlinux.com/reverse-ssh-tunnel-or-connecting-to-computer-behind-nat-router)

Surprisingly, Alexonlinux's solution worked out-of-the-box.

Seeing this, I tried the previous method, this time using Port 6333, but no luck. Then I tried Alexonlinux's method using Port 19999 and again it works fine.

The reason I can't stick to Alexonlinux's solution is, that it requires some commands to be entered on the PC behind the NAT, and that's not possible in my case.

I really wonder what could be stopping the connection when using Fabelier's method. Maybe the script is not loading? I did try manually running the script but still no luck.

I have also set ```
GatewayPorts yes
``` on the PC behind the NAT.

For the record, here's the script I've used from Fabalier's method
```
a=`ps -ef | grep 19999 | grep -v grep`
if [ ! "$a" ]; then
     ssh -fN -R 19999:localhost:22 <middle-usename>@<middle-hostname>
fi
```(obviously I've changed the <middle-usename>@<middle-hostname> to the necessary);) I had to change the first line as brackets were not acceptable.
Would really appreciate some help on this, pls.

---

