---
title: "How to Change name in SSMTP"
date: 2015-10-07
forum: General Help
---

### Post by chiques on 2015-10-07
I have 2 servers. 1 server works great and my newer one has a small issue with ssmtp.

I pretty much copied my 'working' configuration file in /etc/ssmtp/ssmtp.conf on to the new server.

Problem:
When I run:
ssmtp [email]name@mymonitoringemail.com[/email]
"type something here"
CTRL+D

I get this error message in in /var/mail.err

> Oct  6 21:03:12 mylinuxmachine sSMTP[1661]: 550 5.7.1 Authentication is required to send mail as <somenameIdontknow@outgoingserver.net>




Can someone help by giving me a hint on where '**[COLOR="#FF0000"]somenameIdontknow[/COLOR]**' is coming from or where I can set it? I would like to change that to 'somenameIknow'.

_**This make sense since:**_
somenameIdontknow = some random set of characters that I do not know where they came from

somenameIknow = what I wish to set since this is my valid email address

Thanks in advance!

---

### Post by chiques on 2015-10-07
I found my problem.

I had not set the information in /etc/ssmtp revaliases

Once I set my server information in there ssmpt works as expected now. :D:D:D:D

---

