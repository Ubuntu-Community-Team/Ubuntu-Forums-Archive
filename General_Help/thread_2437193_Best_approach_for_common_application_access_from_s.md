---
title: "Best approach for common application access from standard accounts?"
date: 2020-02-19
forum: General Help
---

### Post by bcschmerker on 2020-02-19
**I have an issue to solve as administrator for a new house-of-worship system in the pre-installation programming phase.**  I anticipate both Departments at OMS Japanese Christian Church (Walnut Creek, CA, USA) needing access to OpenLP and a common database of Songs, Bibles, &c. therewith; each Department will have its own standard account on jccwc-audio, with a separate admininstrator account to update this system.  Will OpenLP need its own hidden "public" account, as I am estimating is needed from the application configuration?  (The database defaults to a current-user sub-subdirectory of /home.)  And how will Groups tie in to the necessary User permissions?

---

### Post by wildmanne39 on 2020-02-19
*Thread moved to **General Help a more appropriate sub-forum**.*

---

### Post by bcschmerker on 2020-11-30
**Update:**  Discovered solution on my own -- created a User _openlp_ and Group _openlp_ on jccwc-audio, tied four Users to Group openlp.  From admin account, configured OpenLP to use /home/openlp/local/share/openlp and executed sudo chmod 755 *.* as necessary.

---

