---
title: "Setting up a jabber server"
date: 2005-10-03
forum: General Help
---

### Post by Antithesis on 2005-10-03
Hi there,
I'm trying to set up a jabber server at work - we are all using ubuntu here :)
I've tried to do a test install of jabberd (apt-get worked great, even on 64), seems ok, but I'm having a few problems. I've read the documentation on the jabberd website, but there are still a few things I'm unclear
1) Since this is for inter office use, I want to block all outside traffic (in or out) for jabber - it should only work from inside our intranet - How can I be assured of this?
2) I can succefully add a user if I log into gaim from the machine where the jabber server is installed, and login. However, when I try from another machine, I can't do either.... this is kinda of a big problem.
Also, in general it would be nice if anyone could point me to somewhere to outline installing a jabberd server only used for internal client-server-client communication, and nothing else.

We are currently using hoary, and my jabber server is 1.4.3

Thanks for your help.

---

### Post by teeler on 2005-10-20
Is your hostname set correctly? I found that if you're hostname is set to the default "localhost" and you try to connect it will fail if you're trying to connect remotely - thats kind of a bummer especially if the box isn't named ;)

But hopefully it is! I hope this helps, I was having the same problem and I found the problem by running jabberd from the console & trying to connect. 

Hope this helps.

---

