---
title: "sendmail not honoring my access.db"
date: 2007-08-19
forum: General Help
---

### Post by posterboy on 2007-08-19
OK, I have sendmail working for my domain, I can send and receive mail just fine. Issue: Spammers LOVE to bounce unknown addresses and the bounce message goes to an innocent victim. To stop that, I set up access to DISCARD these emails. This maybe isn't RFC compliant, but, I am a home user, and it works for me. For reasons I cannot determine, while this worked great on FC6, it's as though the access.db isn't being seen at all. There are NO discards in the logs, and in fact a test shows that email to non-existing users DOES bounce. I did make access, as I should, and it said it was updating access.db, but it's not working. Ideas, please?
Thanks

---

