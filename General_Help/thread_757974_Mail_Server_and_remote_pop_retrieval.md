---
title: "Mail Server and remote pop retrieval"
date: 2008-04-17
forum: General Help
---

### Post by TheTouti on 2008-04-17
Hello,

Hope I'm posting this in the correct section.  

I don't really know much about Linux and I'd like to knoiw if (how) this can be done with ubuntu. I have a PC at home (Vista) on which I have a dynamic IP client so I can access it on certain ports.

I installed hMailserver on this and configured it to retrieve the emails from all my pop3 accounts every 10 minutes and put them all in a single mailbox.  From my XP workstation, my laptop and my workstation at work I can access all my emails via IMAP.

So far I know that this can be done if I use getmail or fetchmail to get the emails from my remote pop accounts and place them in the local mailbox.

The part I'm not sure of is about relaying emails.  In my hMailserver setup I created a domain called home.blahblahblah.com which obviously is not registered anywhere and can't be accessed directly from internet.  To connect to my IMAP server I use <whatever>.dynip.com which is my Dynamic IP service and I specify the port that I've assigned to IMAP in hMailserver.  In my mail clients I've configured my SMTP to also use the dynamip IP name and a different port.

Obviously this machine that I run at home cannot send emails directly because my ISP (like most) doesn't allow acces to port 25 so I have to relay the emails through another server to which I have access on a different port.

This is easy in hMailserver because its smtp setup as a "Delivery of email" option where I can specify a host name, smtp relayer, TCP port, enable authentication and specify the username and password.  When this is configured, hMailserver relays all the emails to that SMTP server.

As you've probably guessed already my question is.  Can this be done in Ubuntu and what softwares do I need ?

---

### Post by qhor on 2008-05-05
> **TheTouti said:**
> 
As you've probably guessed already my question is.  Can this be done in Ubuntu and what softwares do I need ?

It is possible, but there's no way that I know which is nearly as easy as hMailserver.

An example of the way to go in Ubuntu would be:
[LIST]
[*]**getmail** to do *POP Retrieval* - storing the emails locally in, say, Maildir format.
[*]**Dovecot** as an *IMAP server* - to serve the emails from the local Maildir store.
[/LIST]
For this part of the problem, see: [the related tutorial on the Gentoo Wiki]("http://gentoo-wiki.com/HOWTO_Fetch_mails_from_multiple_POP/IMAP-mailboxes_and_export_them_via_IMAP_to_Thunderbird/SquirrelMail_etc"). The installation part isn't relevant (you'd want to use *apt-get*, not *emerge*!), but the configuration of Dovecot/Getmail is certainly relevant.


[LIST]
[*]**Exim** (or **Postfix**, or **Sendmail**, or some other MTA) as an *SMTP relay*. This is an almost-separate problem - setting up your MTA to authenticate a user via SMTP, then to relay authenticated users' mail on to your ISP's SMTP server. See this tutorial, for an example with Exim: [SMTP Relaying Via a Smarthost]("http://www.lexspoon.org/linux/smtp-relay.html").
[/LIST]

---

