---
title: "Replacing xserver on running app"
date: 2013-06-28
forum: General Help
---

### Post by Bronie12345 on 2013-06-28
First of all, here's the problem for shorts:
I have a firefox session running on my home server/desktop (ubuntu server 11.04, x86_64).
Currently at my workplace, I'd like to relay the traffic to X from the local X version at the server to Xming on my laptop running windows 7 ultimate (SP1)

Here's the setup:

Server:
Linux Ubuntu Server 11.04
Kernel: 2.6.24-28-server x86_64
X.org X Server 1.10.1 (2011-04-15)
X Protocol Version 11, Revision 0
xorg-server 2:1.10.1-1ubuntu1.3
pixman version 0.20.2
local X: localhost:0
remote X: localhost:10.0

Laptop:
Windows 7 Ultimate x64 (build 7601)
Xming 6.9.0.31
local X: localhost:0

Connection:
SSH (PuTTY 0.62)
X11 forwarding enabled
logged in as "root" on server from laptop

Any suggestions how I can point firefox (the running x-client app) to a different X server?
(so point it to localhost:10.0 instead of localhost:0)

Thanks in advance,
Bronie12345

---

### Post by TheFu on 2013-06-28
I think you can't relay with hops.
Perhaps using NX directly makes sense?  Windows with the client and your home PC with the server?
* NoMachine nx-client for Windows (free)
* FreeNX on your server at home (it uses ssh, so no other ports need to be opened.)  I have port 443 redirected on the router to port 22 on the FreeNX server, since many work and hotels will block almost all ports except 80 and 443.

It is sorta like VNC with a built-in VPN, but I think the NX protocol is 2-3x more efficient. I've used it from all around the world ... literally ... as a remote desktop.

After all, X/Windows is not very efficient over WAN connections.

The NX client install is fairly standard. next, next, next.
The FreeNX server install has some manual steps - took me 15 minutes the first time to generate keys and put the public key on the client machine (inside the nx-client GUI).  If you google "ubuntu freenx", the how-to will be found.


Now for the other "issues":
* 11.04 has been out of support over a year. 12.04 LTS is really what people like you and I should be running.
* running anything as the "root" user except system admin stuff for the specific time goes against best practices. A few apps actually will not run as root, since they know it is a bad idea.

---

### Post by Bronie12345 on 2013-06-28
TheFu,

Thank you for your reply.
I will certainly look into FreeNX and NoMachine nx-client.

For now I've used the session-restore function that firefox has (so I killed it, and used session restore to get everything back on my laptop), but seeming the main question is not resolved yet, I will leave the thread open for now (I still can't relay the actual output to a different server, but perhaps after some experimenting with screen, bash, netcat and pipes I will be so)

The "slowness" and modern "localhost preference" of X is not really a problem for me, seeming I mainly use it to read data and copy-paste between the endpoints.

The main reason the server still runs 11.04 is that somehow 12.04 always behaves unstable with the applications I install by default.
Apart from that: both ubuntu 12.04 and win7 installations on my laptop are in dire need of a fix/reinstall, just like the server (which is also dual-boot win7 and ubuntu 11.04), so I will experiment with setups and configs on one of my test-systems for the coming weeks.

---

