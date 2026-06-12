---
title: "Jabref can't find Java on amd64"
date: 2013-10-19
forum: General Help
---

### Post by WhiteHorse on 2013-10-19
I get the following error when running jabref:
error /usr/lib/jvm/java-6-openjdk/bin/java file not found

Fixed by running the following:
sudo ln -s /usr/lib/jvm/java-6-openjdk-amd64 /usr/lib/jvm/java-6-openjdk

Please move to appropriate category and notify maintainers of jabref.

---

