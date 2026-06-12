---
title: "Kmail, SMTP/POP3 through firewall"
date: 2007-08-25
forum: General Help
---

### Post by anders_ps3 on 2007-08-25
After a couple of days of testing, I have run out of hypotheses - need help

I´d like to use Kmail (KDE, Kubuntu, Feisty, PS3) through a Netgear DG834 firewall/router for email via my provider (telia.com)

From Telia, have gotten:
- username, password
- names of out-server & in-server
- info that out/in should use smtp/pop3 through ports 465/995, respectively
The username is not (part of) my email address. Telia could not say anything about authentication methods

Kmail account settings (let´s for simplicity start with sending emails):

´General´ tab:
Name: (anything)
Host: (name of telias out-server)
Port: 465
Server authentication required flag: checked
Login: (username from telia)
Password: (password from telia)
Store SMTP password flag: checked

´Security´ tab:

SSL encryption chosen
DIGESTMD5 chosen (server support report: PLAIN, CRAM-MD5, and DIGEST-MD5

Over to my Netgear router:
created tcp/POP3 and tcp/SMTP services on ports 995 and 465, respectively
Firewall rules:
Default: block all incoming, allow all outgoing.
added explicitly allowance for outgoing tcp on port 465
similar for incoming tcp on port 995

But..... when I try to send a mail, Kmail regrets its inability to send, and suggests an erroneous password.

Any idas?

---

