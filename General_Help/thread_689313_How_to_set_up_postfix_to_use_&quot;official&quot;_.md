---
title: "How to set up postfix to use &quot;official&quot; SMTP server"
date: 2008-02-06
forum: General Help
---

### Post by wirawan0 on 2008-02-06
I want to use postfix on my laptop, since it allows queueing outbound mail. I am not always connected to outside network, you know, and I want to be able to write and "send" emails when I'm offline. The idea is that the mail will be sent off when the computer is connected to the network.

I think, the way to do this is to configure postfix to pass the outbound mail to a known SMTP server, to which I have an authorized access. For example, an SMTP server of my university, or of google (you can do this if you have gmail account). This is what I mean with "official" SMTP server in the title, since it is acknowledged as a legitimate SMTP server on the world wide network. How to do this with postfix? SMTP servers nowadays have username and password authentication also. If any of you is an expert (or at least more knowledgeable than I am) on this matter, please give a pointer. The manual for postfix is so long and I'm swamped reading it.

Wirawan

---

### Post by wirawan0 on 2008-02-13
Grrrh... No one really cared about this question. Come on, this is not that hard for experts!

I finally found several useful documents on the web which answered my own question. I would use gmail smtp service (which is free if you have an account with them) as my test bed. Other hosts can use similar strategy; but on the way I found that this SMTP-authentication thingy is a can of worm--lots of possibilities in there, which can cause you headache (read: steep learning curve).

[http://www.postfix.org/TLS_README.html](http://www.postfix.org/TLS_README.html)
[http://souptonuts.sourceforge.net/postfix_tutorial.html](http://souptonuts.sourceforge.net/postfix_tutorial.html)  >> excellent tutorial on using postfix with gmail, although needs updating for newer postfix

And for reference, always have this page open:

[http://www.postfix.org/postconf.5.html](http://www.postfix.org/postconf.5.html)

But after all these, the success came from many trial-and-errors. I had to let postfix dump verbose messages to my log.

Anyway, I will write out a short how-to after the day subsides to provide other users guidance on how to use postfix on their laptop.

Wirawan

---

### Post by discodan on 2008-02-13
Dear Wirawan,

Thank you very much for posting this.  I've been scratching my head over this.  I'm trying to setup a 7.10 server so that it will email logs and admin alerts to me using an "official" smtp server.

I'm glad to hear I'm not the only one having trouble with this.

I suspect that the problems I am having have to do with required authentication on the external smtp server.  So any info or advice you can provide regarding your solution would be greatly appreciated.

sincerely,

disco

---

