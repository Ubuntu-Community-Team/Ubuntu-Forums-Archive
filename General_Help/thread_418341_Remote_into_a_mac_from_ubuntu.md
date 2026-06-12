---
title: "Remote into a mac from ubuntu?"
date: 2007-04-22
forum: General Help
---

### Post by jordn on 2007-04-22
Hi there,

i'm just about to throw together a computer for feisty. i was wondering  if it would be possible to remotely access a Mac that i have on my home network via rdesktop or similar, and use it to run its (that is, the Mac's) applications?

i was looking at the Seamless Virtualisation thread in the Ubuntu documentation section:

[https://help.ubuntu.com/community/SeamlessVirtualization]("https://help.ubuntu.com/community/SeamlessVirtualization")

would it be possible to remote into the Mac (i.e. set up Chicken of the VNC or Apple Remote Desktop) and connect to it using a linux VNC program?

thanks in advance,

jordn.

---

### Post by jordn on 2007-04-23
any takers? :)

---

### Post by gupi-gupi on 2008-03-28
I'm in the same situation, anyone?:)
I noticed this: [https://help.ubuntu.com/community/AppleRemoteDesktop](https://help.ubuntu.com/community/AppleRemoteDesktop)
but I'd like to be able to wiew the leopard desktop like in virtualized machines in my ubuntu screen. something like: [http://lifehacker.com/software/how-to/remote-control-leopard-with-tightvnc-319528.php](http://lifehacker.com/software/how-to/remote-control-leopard-with-tightvnc-319528.php) , but for linux.

---

### Post by eriqjaffe on 2008-03-28
Apparently, Panther has a VNC server built in, although Apple doesn't really advertise it.

[http://lifehacker.com/software/how-to/remote-control-leopard-with-tightvnc-319528.php](http://lifehacker.com/software/how-to/remote-control-leopard-with-tightvnc-319528.php)

They show OSX being controlled in XP, but I see no reason why you couldn't control it with pretty much any Linux-compatible VNC viewer.

---

### Post by gupi-gupi on 2008-03-28
I found this post [http://www.lynchconsulting.com.au/blog/index.cfm/2008/1/31/OS-X-Leopard-and-Ubuntu-Screen-sharing--HOWTO](http://www.lynchconsulting.com.au/blog/index.cfm/2008/1/31/OS-X-Leopard-and-Ubuntu-Screen-sharing--HOWTO) and seams intresting, I just don't know how to use it to connect from outside the local lan, the command: $ xtightvncviewer 192.168.0.55 is good for an internal lan I guess, but how to do it from outside? and how secure is it?:)

---

### Post by gupi-gupi on 2008-03-28
ok maid it :lolflag:
I told my friend to port forwarding on the the roouter the 5900 to 5903 tcp/udp and open the firewall on those doors and than I entered:   xtightvncviewer 79.xxx.xxx.xxx the router ip and that maid it
[[IMG]http://img221.imageshack.us/img221/646/leopardonremotedj4.th.gif[/IMG]](http://img221.imageshack.us/my.php?image=leopardonremotedj4.gif)

only problem is that it's damm slow to load... but worked!

---

### Post by NeoGreen on 2008-04-23
Cool.  I setup a connnection from my house to my Mac using VNC.  I first VPN to my job then connect to my Windows Machine then connect to my Mac.  I am still trying to find a way to remote desktop to a Mac from a Windwos machine.  I used VNC but it's just too slow when vpned into the network.

---

