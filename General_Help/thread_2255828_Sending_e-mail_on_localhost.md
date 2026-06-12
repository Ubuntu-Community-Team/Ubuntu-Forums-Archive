---
title: "Sending e-mail on localhost"
date: 2014-12-07
forum: General Help
---

### Post by deb2 on 2014-12-07
Do mail transfer agents use /etc/hosts when you send e-mails or do they consult with an external DNS? I set up ISPConfig, SquirrelMail, Postfix and Dovecot and saved a fake domain into the hosts file "127.0.0.1 _[COLOR=#0066cc]example.com[/COLOR]_" in order to see if everything was working correctly. In ISPConfig I set up the domain (_[COLOR=#0066cc]example.com[/COLOR]_) and e-mail account ([EMAIL="jonsnow@example.com"]jonsnow@example.com[/EMAIL]). When I send a test e-mail from "[EMAIL="jonsnow@example.com"]jonsnow@example.com[/EMAIL]" to "[EMAIL="jonsnow@example.com"]jonsnow@example.com[/EMAIL]" it doesn't get delivered to the mailbox and no error is returned. This makes me wonder whether the MTA realises that the domain name isn't supposed to be on the Internet but on localhost. My web browser realises that "_[COLOR=#0066cc]example.com[/COLOR]_" is on my computer and not on the Internet.

I would have used "localhost" instead of "_[COLOR=#0066cc]example.com[/COLOR]_" but ISPConfig returns "Invalid domain name." when I try to add it.

---

