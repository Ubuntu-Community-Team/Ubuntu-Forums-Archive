---
title: "$DISPLAY, remote host"
date: 2023-07-30
forum: General Help
---

### Post by ulrichmuc2 on 2023-07-30
I log in via ssh -Y to a remote host from my ubuntu PC with IP-address 192.168.2.137.
On the remote host I say "export DISPLAY=127.0.0.1:10.0" and can run applications with gui.
ping  192.168.2.137 works as expected.

However, when I try "export DISPLAY=192.168.2.137:10.0" and try to run a gui-application,
I get  "cannot open display: 192.168.2.137:10.0".

Explanation anybody?

      ulrich

---

### Post by TheFu on 2023-07-31
ssh -Y sets up an ssh tunnel just for X/Windows traffic. That tunnel makes X believe it is sending X/Client stuff to the localhost, i.e. 127.0.0.x/8, so it works.

If you don't want to use ssh tunnels and want to use straight X11 protocols with all the terrible security aspects, then you need to allow the remote X/Client access to your X/Server by running an xhost command on the server and setting the DISPLAY  on the X/Client system to point at the IP of the server.  Before we had ssh X11 Forwarding, we had to do this manually ... usually people would setup their .login shell to figure it out.

I don't know when, but perhaps 10-20 yrs ago, X/Windows added an "authorization" file to prevent other users on the remote system from sending traffic to other X/Servers.  Before that was built-in, we'd screw with other people on large LANs, since X/Windows uses UDP and there's not need for the "source" to be correct in the transmissions.  Spoofing X-traffic was common.  I worked on place where we'd change the background on other people's workstations slightly over their shift.  It may start with a dark gray background, but a few hours later, it would be bright orange.  This was possible because they'd done the 'xhost +' command and not a more specific one that also included the authorization cert.

I'd happy sell you my 7 book collection on X/Windows Programming for $200. You pay for shipping too. They've been in a box in a closet since the mid-1990s.  Each book is 2-5cm thick and full of details very few people need to know anymore, especially with Wayland moving towards production quality in the next 10 yrs.

---

