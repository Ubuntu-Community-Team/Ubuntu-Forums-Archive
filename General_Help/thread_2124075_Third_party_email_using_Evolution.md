---
title: "Third party email using Evolution"
date: 2013-03-09
forum: General Help
---

### Post by dah2 on 2013-03-09
I have no idea where to go for an answer to this question, so I thought I'd start here.  I'm having trouble configuring Evolution to send email through Comcast server and my personal site server.  Let me try to clarify...

Comcast is my ISP. I have a personal web page and associated email accounts that I prefer to use.  At the moment, I use three such email accounts, all at the same site. I have been using Evolution as my deskto email client.  I was using ports 110 and 25 to send/receive email (bad idea, I know). Comcast no longer allows access to those ports, so I had to switch to SSL, ports 995 and 465. I can set up my Comcast email in Evolution to send and receive fine.  I can set up my other personal accounts to receive email, but I can't successfully configure to send them via the Comcast server. Here's the configuration I understand needs to be used (though I've tried a variety of configurations):
- Identify tab
  - email address: <personal site address>
  - Reply-To: <personal address>
- Receiving Email tab
  - Server Type: POP
  - Server: <personal site server>, Port 995 (prescribed by both personal site and Comcast)
  - User name: <personal address>
  - Security: SSL encryption
  - Authentication Type: Password (remember password checked)
- Sending Email tab
  - Server Type: SMTP
  - Server: smtp.comcast.net
  - Port: 465
  - Server requires authentication: checked
  - Security: SSL encryption
  - Authentication Type: Login
  - User name: <personal address> (remember password checked)

I'm on Ubuntu 12.04 and Evolution version 3.2.3.

If you have any thoughts, I'd greatly appreciate hearing them.  If you know of a better place where I can ask the question, please let me know that, too. I'm not averse to changing email clients if that's the only recommendation I can get. 

Thanks....Dale

---

### Post by gifford on 2013-03-09
Have you tried on SMTP: Security=No encryption.
This link might help: [http://askubuntu.com/questions/159584/evolution-sending-email-settings](http://askubuntu.com/questions/159584/evolution-sending-email-settings)

---

