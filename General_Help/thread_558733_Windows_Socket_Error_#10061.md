---
title: "Windows Socket Error #10061"
date: 2007-09-24
forum: General Help
---

### Post by shanepardue on 2007-09-24
I have ejabberd set up on an Ubuntu server and many of my clients are connecting via Windows XP. 
For some reason, at what appears to be random times, a client will get the error message "Windows 
Socket Error #10061". It's not network-wide as some people are connected when the client receives 
this message. Once this client receives this error message, he/she usually can't connect for a few 
minutes, sometimes hours. After awhile, they can connect without a problem.

I know it's not necessarily a configuration error and the server or client is not behind a firewall.

Any idea why this is happening? Thanks in advance for your help!

---

### Post by ddrichardson on 2007-09-24
10061 is an active refusal from your server. If this is a local network I'd be looking at using traceroute from the problem machines to see if there is a packet collision problem - perhaps a hub where there should be a router or switch.

Is there any additional error message - usually a hex code?

---

### Post by shanepardue on 2007-09-24
> **ddrichardson said:**
> 10061 is an active refusal from your server. If this is a local network I'd be looking at using traceroute from the problem machines to see if there is a packet collision problem - perhaps a hub where there should be a router or switch.

Is there any additional error message - usually a hex code?
The traceroute just shows it going straight to the chat server. I can ping the server just fine 
also, but when Pidgin (or PSI) try to connect, I still get that socket error. Unfortunately, there 
isn't any more error message.

I've also noticed that I can reproduce the problem (without randomness) by logging in with a 
user account that has never logged in before. That new user will get the error message at first, 
but a few minutes later, is logged in and happy.

---

### Post by ddrichardson on 2007-09-24
There are a lot of posts on the net realating to an XP update in April causing this, but I think they're a red herring as they relate to Outlook Express.

---

### Post by shanepardue on 2007-09-24
I'm running out of ideas. I've heard situations involving norton antivirus and of course 
firewalls, but this case seems to be unique in that it can't be tied to a particular app or 
configuration error. The thing that really throws me off is the fact that I can ping it, but I 
can't connect to it for a couple minutes (on initial login).

---

### Post by ddrichardson on 2007-09-24
Me either - I've spent the last while searching through MSDN, it doesn't make any sense. Can we lock this down to an Ubuntu server, is there a Windows server you can attempt an initial connection on?

---

### Post by shanepardue on 2007-09-24
> **ddrichardson said:**
> Me either - I've spent the last while searching through MSDN, it doesn't make any sense. Can we lock this down to an Ubuntu server, is there a Windows server you can attempt an initial connection on?
I don't have that capability as of right now, but I'm beginning to think it is a server 
configuration error as that error message usually refers to a "refused connection". I'm 
going to screw around with it's configuration and possibly even switch server software 
and see if that changes anything.

Thanks a lot for your help so far and I'll continue to keep you updated. You've been a 
great help!

---

### Post by shanepardue on 2007-09-29
After countless hours spent for nearly a week, I decided to install openfire 
on a Fedora Core machine and am happy to say it worked perfectly. There 
is something in a windows network (possibly active directory) that Ubuntu 
would not play nice with. Fedora has answered the call and is running our 
chat server perfectly..Thanks again for everyone's help!

And for the record, I still prefer Ubuntu for a desktop environment any day, 
but it seems in this rare case, another distro will suit my needs. Thanks for 
your help!

---

