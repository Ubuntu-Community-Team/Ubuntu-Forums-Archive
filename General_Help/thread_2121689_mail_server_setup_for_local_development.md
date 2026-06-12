---
title: "mail server setup for local development"
date: 2013-03-02
forum: General Help
---

### Post by lancsDavid on 2013-03-02
[ common question i know but i've spent 3 days looking for answers, unsuccessfully ]

on my old windows box i set up a WAMP server & had a program called Argosoft mail server.  with this, when i was building & testing drupal sites locally, i could send mail from within drupal (such as notification emails for new users) & access them via Outlook Express.   i had a bunch of users - admin@localhost, bob@localhost, jane@localhost, etc - & i think SMTP was used somehow (though i'm not sure. nor if it was authenticated)

[ as might be clear, i never actually knew the proper in's & out's of how the whole thing worked, which was a bit annoying.  but at least it worked ]

trying to replicate this in Ubuntu is proving tricky.  i figure i need Postfix (to do argosofts job) & Evolution (to do what Outlook Express did) & maybe something called Dovecot.   but as for what exactly is going on, configuring them to work (with localhost) & actually getting them working, i'm drawing a bit of a blank at the minute

i've got hold of a Postfix book & am working through it but its a long read & most of it isn't relevant (so its doing little but distract me & sap my concentration)

any help much appreciated

david

---

