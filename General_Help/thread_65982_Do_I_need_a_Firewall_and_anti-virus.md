---
title: "Do I need a Firewall and anti-virus??"
date: 2005-09-15
forum: General Help
---

### Post by 68Firebird on 2005-09-15
Sorry for all these questions but it is the only way I am going to learn. 
I have yahoo dsl and the modem is conected directly to my pc, No router.

Do I need to install a firewall?? I know the answer would be yes in windows but not sure about Linux. And do I need a virus scanner for Ubuntu?

---

### Post by Leif on 2005-09-15
no, you don't need either the way ubuntu is set up by default. if you install sevices that open your pc to the outside world (ssh, ftp etc.), however, you may consider installing a firewall - but you will still be a lot safer than on windows. i personally have neither installed.

---

### Post by az on 2005-09-15
You do not need anti-virus software, either.

If you are in doubt about a particular application you would like to install, and are not sure if it open any ports (communicates with the internet) and puts your computer at risk, just ask about it here on the forums.

---

### Post by mcmuffy on 2005-09-15
You only really need a virus scanner if you have files comming in that will end up on a windows box. If you feel one is needed give clamav a try, there are a number of gui frontends for it you can use.
As for a firewall, again not strictly needed but firestarter is pretty good if you want to give one a try.

---

### Post by 68Firebird on 2005-09-15
Thanks for all the quick replys  :) 
 I have nothing that I know of that would put the Ubuntu install at risk so i'll do without the firewalls and anti-viruses for the time being.

---

### Post by uglysmurf on 2005-09-15
I haven't had much need for virus protection either, but I've been using Firestarter as my firewall and love it so far, relative to the various junk I used back in my Windows days...

Even with a hardware firewall (like a router) sitting between you and the world, a software firewall doesn't hurt for lots of reasons...when the time comes, try firestarter...

---

### Post by 68Firebird on 2005-09-16
[QUOTE=uglysmurf]I haven't had much need for virus protection either, but I've been using Firestarter as my firewall and love it so far, relative to the various junk I used back in my Windows days...

Even with a hardware firewall (like a router) sitting between you and the world, a software firewall doesn't hurt for lots of reasons...when the time comes, try firestarter...[/QUOTE]

Thanks for the info. I installed it and it is fun to play around with it. I went to Shields up and did a port test and no ports were stealthed. Then I enabled firestarter and blocked all icmp pings and ran Shields up again. Passed, True stealth analysis.  :) 

Looks like firestarter does a good job.

---

### Post by gazz on 2005-10-15
> Then I enabled firestarter and blocked all icmp pings and ran Shields up again. Passed, True stealth analysis.

Ubuntu truly rocks! :p  

I installed it two days ago on a test machine and everything went pretty smooth. Finding out how to connect to the internet via adsl, was pretty difiicult though, until I stumbled over the magic words pppoeconf, which did the trick.

I have installed Firestarter and made some policies, but when I test the firewall at Shields up I fail because my machine responds to port 80 and 443: "Your computer has responded that this port exists but is currently closed to connections."

How do I block all icmp pings?

Thanks

---

### Post by Darrin on 2005-10-31
I ran stealth test both with and without the firestarter firewall. Everything was stealthed either way.
0 Ports Open
0 Ports Closed
1056 Ports Stealth
---------------------
 1056 Ports Tested

Maybe because I have a router?
Doesnt look like I need a firewall?

---

### Post by Doc.Caliban on 2005-10-31
One feature that I really miss in regards to a firewall from my Windows experience, is having total control over outgoing traffic.  The firewall I used in Windows would ask me for permission for each process that tried to access the net.  (you could tell it to save the choice so it didn't ask you again.)

There are a few Windows apps that I still run via Wine/Crossover Office that I know access the net, but I don't want them to.  Not only those, but I'd like to know when any app tries to do so.  (I'm a bit of a network control freak)

I know that Firestarter can set rules for outgoing connections, but I don't believe that it will dynamically build those rules by querying me to define them on an incident by incident basis.

Is there something that will?

Any suggestions?

Regards,

-Doc

---

