---
title: "Is it possible with Postfix Forwarder?"
date: 2015-11-28
forum: General Help
---

### Post by albert41 on 2015-11-28
Hi,
I was wondering if its possible to forward all the sent emails using Postfix Forwarder package or is there another package that can do that?

I would like to use postfix forwarder on pfSense which already has the package version 2.4.6 but if its better on installing ubuntu on hyper V i have no issue either.


Currently the company uses godaddy domain with the workspace emails and they use pop because it saves the pst files while IMAP saves the sent on the server, but there is limited space. And on the godaddy workspace email I can forward all the inbox emails to another email no issue just the sent part cannot. I also called godaddy to see if they could guide me though they did tell me i would need to add the mx records with the email and password of the account i would want to BCC the send emails on the configuration of postfix forwarder. While someone else on another forum did mention that i would need to change my mx records to point to my WAN ip (pfsense) but not sure why or am i understanding incorrectly?


See picture for example

Thank you[ATTACH=CONFIG]265815[/ATTACH]

---

