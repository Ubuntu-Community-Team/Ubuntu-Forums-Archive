---
title: "can't access Maildir via mail client from other machines"
date: 2007-09-04
forum: General Help
---

### Post by daveh0 on 2007-09-04
Greetings,

Ubuntu Server - Feisty Fawn.

I am running fetchmail to download mail from a pop3 account with my web host. I am also running Dovecot to make the mail available as IMAP mesages  to other machines on my LAN.

On the box running fetchmail and dovecot, I can successfully connect (using 'localhost' or the IP for incoming mail server) and see the messages using Evolution for my mail client.

However, when I try to do the same using Outlook or Thunderbird on my WinXP machine, I get an error saying that it could not conect to the server.

Exact error message from Outlook:

> Cannot connect to the server. If you continue to recieve this message, contact your System Administrator

I can ssh to the box running fetchmail and dovecot so it is accepting some types of connections...

Is there some configuration that I am missing that will allow other computers to connect to Dovecot?

---

