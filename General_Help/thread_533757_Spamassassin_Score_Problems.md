---
title: "Spamassassin Score Problems"
date: 2007-08-24
forum: General Help
---

### Post by Blairboy on 2007-08-24
Ok, despite having edited my /etc/spamassassin/local.cf to include "required_score 5.0", spamassassin still has a required score of 6.31 before it will mark something as spam.  Any ideas on how to fix this?


Turns out it was an issue with amavis taking over the setup of spamassassin.  Just had to edit the debian defaults config file in amavis.

---

