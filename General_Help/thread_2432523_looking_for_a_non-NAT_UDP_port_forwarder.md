---
title: "looking for a non-NAT UDP port forwarder"
date: 2019-12-03
forum: General Help
---

### Post by Skaperen on 2019-12-03
a NAT port forwarder changes the destination address but not the source address.  it works by being in the path of the traffic and intercepting the UDP datagram destined for somewhere else.  what i want is something that can *be* the destination.  that is, if it runs on host 192.168.1.25 and listens on port 3456. then clients would send their UDP datagrams to 192.168.1.25:3456 (not somewhere else).  this program is configured with an IP address and port where to send them to and keeps a map of clients to source port it is using for that client an its source port.  it would change both the destination and source just as if (and probably actually doing so when run as a userland process) it opens a whole new "connection" (socket binding) to send the data through.  this could easily be done for TCP with data streaming, but i need to do this with UDP.  in the way-off future, i think i will also need to do this with SCTP.  i already have a program to forward TCP like this.  i likely will need to modify it, so source code in C or Python is preferred.  ssh does something similar with TCP and unix sockets when forwarding through the ssh connection.  google shows me lots of router based tools that intercept packets not destined for themselves and only change the destination.  basically, i'll be creating what looks like a UDP based server (such as DNS or NFS) one one host but another host forwarded to is really doing the service (or there is a chain of this).

---

### Post by SeijiSensei on 2019-12-03
Would this work?

[https://github.com/troglobit/uredir](https://github.com/troglobit/uredir)

I was going to suggest using xinetd, but it only proxies TCP packets.

---

### Post by The Cog on 2019-12-04
Have a look at socat: [http://docs.byteme.org.uk/cgi-bin/man/man2html?1+socat](http://docs.byteme.org.uk/cgi-bin/man/man2html?1+socat) and [https://medium.com/@copyconstruct/socat-29453e9fc8a6](https://medium.com/@copyconstruct/socat-29453e9fc8a6)
I think this will probably do what you want. You will want the **fork** option to allow multiple concurrent connections.

---

### Post by HermanAB on 2019-12-04
Netcat (nc) and socat can both do what you need

---

### Post by Skaperen on 2019-12-04
i tried [COLOR=#0000cd][FONT=courier new]**socat**[/FONT][/COLOR] but i could not get it to go bi-direction without specifying addresses in both directions.  i'll look into the fork option, but i don't want a 100 process running for 100 "connection".  i've used [COLOR=#0000cd][FONT=courier new]**netcat**[/FONT][/COLOR] for TCP before (it was awkward to set it up) but i'll have to try it on UDP.  [COLOR=#0000cd][FONT=courier new]**uredir**[/FONT][/COLOR] looks interesting.  if i had more time, i'd just code it myself (BTDT for TCP).

---

### Post by The Cog on 2019-12-04
With socat, I imagine that the first address would be UDP-LISTEN:<port>. Second address would be UDP:<host>:<port>.
You need fork if you are going to support more than 1 concurrent connection. 
So a one-liner might look like:```
socat fork UDP-LISTEN:<port> UDP:<host>:<port>
```

---

### Post by Skaperen on 2019-12-04
if i develop my own, it will do its thing all in one process w/o even using threads.  then i will add on a control channel to allow an operator to stop or start any specific forwarding, or list them with stats.  then i will leave it up to someone else to make a fancy GUI.  i would try to do TCP, UDP, and SCTP all in one (so each start line would need a protocol parameter).

i could see the value in doing this over a secure tunnel, but *OpenVPN* or *SSH* can add this.  i did create a tool to transfer files between two remote hosts securely, done entirely in [COLOR=#0000cd][FONT=courier new]**bash**[/FONT][/COLOR] (uses [COLOR=#800080][FONT=courier new]**openssl**[/FONT][/COLOR] and [COLOR=#800080][FONT=courier new]**socat**[/FONT][/COLOR]).  that can probably be torn apart to build a one-port tunnel.

i'll do some more experimenting and exploring with [COLOR=#0000cd][FONT=courier new]**socat**[/FONT][/COLOR].  and i might have found something usable in pypi.

---

### Post by The Cog on 2019-12-05
That sounds like a big and interesting project. I can see how you could do it single threaded with lots of select calls. And you could be sure that the UDP forwarding didn't ever coalesce two close-together UDP packets into one, whereas socat doesn't seem to guarantee that in the docs - it all talks about streams, so it's possible it would lose the UDP packet delimiters.

I do think I see an easier way if you are prepared to accept a NAT solution though. You just need two separate NAT entries. One in the PREROUTING chain doing DNAT to change the destination address, and one in the POSTROUTING chain doing MASQUERADE to fix up the source address. I'm pretty sure that MASQUERADE would change the source port when necessary to avoid duplicates.
Edit: And enable IP forwarding, of course.

---

### Post by Skaperen on 2019-12-06
i have used [COLOR=#0000cd][FONT=courier new]**socat**[/FONT][/COLOR] for SCTP which has boundaries (delimiters) but i did find that [COLOR=#0000cd][FONT=courier new]**socat**[/FONT][/COLOR] was just doing a single steam over only one virtual sub-channel of SCTP.

i should dig out that TCP-only implementation i made and see how hard it might be to make a UDP-only version and a UDP+TCP version.  the source port number on the upstream side would just be whatever the system picks relative to that address+protocol.  that, and i need to learn what is involved in SCTP protocol-family programming in the Unix socket API.  i have heard the is a reliability layer added to UDP for some applications that need it.  i have also heard of streams over UDP and wonder if is part of RUDP or uses RUDP,

*more*:

i cannot find the original one-process version from around 1998, but i did find the version i made in 2002 to demonstrate how to use my daemon library API.  the daemon library forks each incoming connection and returns in the child process (again for each connection, in a new process) to the caller, which is the implementation code.  so this is the forking version.  but i did make a non-forking version that was all centered around one select() call that waited for everything.

since i could not find this 20 year old code on my laptop i gave google a shot to see if it got archived anywhere (not sure if i ever released it) and found what i need that someone else implemented in python (my preference these days).  it is called [COLOR=#b22222][FONT=courier new]**udprelay**[/FONT][/COLOR].

---

