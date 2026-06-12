---
title: "Email holding up windoze purge"
date: 2007-09-05
forum: General Help
---

### Post by weekdaysailor on 2007-09-05
I'm dual boot, and a NOOB that would like to ditch windoze but may have to abandon Ubuntu if I can't get the final piece - email. We use Exchange (ok, that's easy you say) - but we authenticate using RSA tokens for our internal OWA URL (so my normal password won't work) - it doesn't appear that any of the email clients have particularly sophisticated authentication when it comes to Exchange.

Googling isn't getting me very far - anyone have a thought? We have a lot of happy OSX users, so apparent Apple mail works fine. 

TIA

-WDS

---

### Post by p_quarles on 2007-09-05
Unfortunately, Exchange servers won't be compatible with open source software until MS releases the specs . . . and I wouldn't hold my breath. 

If you have the authority and/or time to replace Exchange with something like sendmail or postfix, you'll be able to get a great cross-platform mailserver. If not . . . sorry.

---

