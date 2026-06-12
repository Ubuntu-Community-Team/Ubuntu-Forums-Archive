---
title: "How to move Postfix mail into /dev/null?"
date: 2008-05-06
forum: General Help
---

### Post by s0n|k on 2008-05-06
I need to move all incoming Postfix-imap emails directly to /dev/null. How can this be accomplished?

---

### Post by Monicker on 2008-05-06
I've used this method before, for select accounts.

[http://forums.devshed.com/mail-server-help-111/postfix-send-mail-to-dev-null-howto-362743.html]("http://forums.devshed.com/mail-server-help-111/postfix-send-mail-to-dev-null-howto-362743.html")

Why do you want to send all email to /dev/null ?

---

### Post by s0n|k on 2008-05-06
sweet. that worked great. i'm testing something that sends thousands of emails per hour, and i don't care about the output. a 10gb hdd won't go very far :p

thanks again

---

