---
title: "Encrypted email"
date: 2005-04-27
forum: General Help
---

### Post by fire59 on 2005-04-27
Recently I've setup passwordless ssh for my server.  I'm wondering if this is the culprit of my encrypted email problem. After doing some email test using PHP it seems like my email are encrypted.  If this is the problem is there a way to turn this off? Would this be in apache2 setting or PHP?

---

### Post by nocturn on 2005-04-28
SSH is not related to mail encryption.  This is done with SSL or PGP.
What mail system are you using?

---

### Post by fire59 on 2005-04-28
Oh..I also just enabled ssl module for apache.  Not exactly sure what mail system i'm using.  I'm assumming postfix since that's installed.

---

