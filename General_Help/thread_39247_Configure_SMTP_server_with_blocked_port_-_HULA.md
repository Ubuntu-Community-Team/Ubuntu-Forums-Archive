---
title: "Configure SMTP server with blocked port - HULA"
date: 2005-06-03
forum: General Help
---

### Post by kgreiner on 2005-06-03
I have Hoary set up at home on a desktop and a laptop, everything works great. But I got adventurous and got the Hula server from svn (current version r230). 

I have incomming email working, local email (send and recieve), but I can not get outgoing email to work.

my isp is Yahoo/SBC DSL. I have a dynamic IP address. My domain name is registered with one of the dynamic dns services. so i can email myself to me (at) myhost.dynamicip.net.

But once i try sending an email from the web interface it goes no where.

I can see that the message tried to send an email (netstat -a) but it just times out.

If i try to telnet to the smtp port of some domains the connection times out. The only smtp ports i can telnet to are my isp and localhost.

I found out that SBC/Yahoo block port 25 (the smtp port).

How can I configure Hula to send all mail to my isp smtp server instead of to who evers i am send email to?

---

