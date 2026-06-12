---
title: "Ubuntu software or Software updater"
date: 2019-04-03
forum: General Help
---

### Post by cam17 on 2019-04-03
If I go to "Ubuntu software" and click on updates on a 18.04.1 new install it responds with "Software is up to date" but if I go to "software updater" it tells me "updated software has been issued since Ubuntu 18.04 was released. Do you want to install it now" followed by the size of the download 376.2 MB.  I though both served the same function when it came to updates. Can any one tell me why the difference in detecting updates between the 2 applications?

---

### Post by Impavidus on 2019-04-03
Maybe one of them listed the available updates before checking for them and the other listed them after checking?

Rule of thumb: when a simple and a complex tool disagree, believe the simple tool. Where "simple" means "designed to do one thing and do it well", not "having an intuitive user interface". Ubuntu software tries too hard to be newbie-friendly. It hides technical details and is less useful when something unexpected happens. I think that most advanced users don't use it.

---

### Post by cam17 on 2019-04-06
No. that is not the case. I tried a new install of Ubuntu and did the same test.  If I go into "Ubuntu software" it does not show any updates. But if I go into "software updater" it shows over a meg of updates.

---

### Post by Rubi1200 on 2019-04-06
Perhaps it is a syncing issue?

I noticed the same thing on a clean install but now after a few hours both act "normally".

---

### Post by Autodave on 2019-04-06
I generally don't trust or use the software center.  If I am in doubt, I still do it the old fashioned way:

sudo apt-get update
sudo apt-get upgrade

---

