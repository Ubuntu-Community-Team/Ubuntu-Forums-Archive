---
title: "Evolution Modifies SMTP Server Config"
date: 2007-12-26
forum: General Help
---

### Post by shutslar on 2007-12-26
I have been using Ubuntu since Breezy.  I just completed a fresh install of Gutsy and love it.  When I set up evolution, I configure outgoing mail like this:

Server Type:  SMTP

Server Configuration
Server:  mail.*mydomain*.com:26             <--My ISP has port 25 blocked and my mail server listens on port 26 also

My POP server is also mail.*mydomain*.com

I get connected to receive mail.  But it does not connect to send mail.  It gives the following error message which is completely confusing me:
> 
Host lookup failed:  smtp.mydomain.com: Name or service not know.

This is confusing because I have my configuration pointing at mail.mydomain.com and not smtp.mydomain.com (mail.mydomain.com is the correct config for my mail server).  I can telnet to my mail.mydomain.com:26 just fine.  I just cannot seem to get evolution to use the right server name.

Any suggestions?

---

