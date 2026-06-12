---
title: "Problem connecting to IRC"
date: 2006-11-04
forum: General Help
---

### Post by Belathor on 2006-11-04
I can't seem to be able to connect to an irc server. I've tried both Gaim and xchat and neither allow me to connect. All it tells me is this:

> Looking up irc.ubuntu.com
* Connecting to chat.freenode.net (213.92.8.4) port 6667...

and then nothing happens past that point. ](*,) 

What could possibly be going on?

---

### Post by prs on 2006-11-04
Have you tried any other addresses? irc.freenode.net for example.

---

### Post by Belathor on 2006-11-04
Yes, I have. I have the difficulty on irc.freenode.net.

---

### Post by KaroSHi on 2006-11-04
have you allowed port 6667 in your firewall/router ?

---

### Post by Belathor on 2006-11-04
hmmm... That is a good question. I turned off firestarter to make sure it wasn't that, but I didn't think about my router. I'll mess around with that!

Thanks!

---

### Post by Belathor on 2006-11-04
So far I haven't had any luck. I tried opening port 6667 to my network address. That didn't work (I'm not sure if I have the right address, but it is the only IP address that I could find). I tried setting my computer up in the "DMZ", but that didn't work, either.

EDIT: I even unhooked myself from the router and connected myself directly to the school network. Yet, it still doesn't work. I'm not sure what is causing this. The Technology department says that there shouldn't be any problems connecting to irc over the school network.

---

### Post by Belathor on 2006-11-04
grr... still no luck. I would really like to get it working so I can use the live support at #ubuntu.

---

### Post by prs on 2006-11-04
That's weird, since it looks like a trace from you to irc.ubuntu.com points to a freenode address. Is the problem only limited to freenode or any other irc-servers? Do you get any response in the status windows in your irc client? 

When I connect with Xchat I get these at first:
* Looking up irc.freenode.net
* Connecting to chat.freenode.net (130.239.18.172) port 6667...
* Connected. Now logging in...
* *** Looking up your hostname...
* *** Checking ident
* *** Found your hostname

And then after a few seconds:
* *** No identd (auth) response
* Welcome to the freenode IRC Network prs
* Your host is leguin.freenode.net[leguin.acc.umu.se/6667], running version hyperion-1.0.2
* *** Your host is leguin.freenode.net[leguin.acc.umu.se/6667], running version hyperion-1.0.2

---

### Post by Belathor on 2006-11-04
I can't seem to connect to any server. This is all the text I see:

> Python interface loaded
 Perl interface loaded
 Tcl plugin for XChat - Version 1.60 
 Copyright 2002-2005 Daniel P. Stasinski
 [http://www.scriptkitties.com/tclplugin/](http://www.scriptkitties.com/tclplugin/)
 Tcl interface loaded
 xchat remote access loaded successfully!
* Looking up irc.ubuntu.com
* Connecting to chat.freenode.net (140.211.166.3) port 6667...

---

### Post by Belathor on 2006-11-04
oops

---

### Post by Belathor on 2006-11-10
Just to let everyone know: The port is blocked by the network. :(

---

