---
title: "Feisty: Apache2 Rotatelogs failed unexpectedly"
date: 2007-07-02
forum: General Help
---

### Post by Erik-NA on 2007-07-02
Using the following directive in the apache2 config gives the error "piped log program 'rotatelogs /var/log/apache2/accessl_%Y%m%d.log 86400' failed unexpectedly"

CustomLog "|rotatelogs /var/log/apache2/access-ssl_%Y%m%d.log 86400" combined

Using Apache/2.2.3 (Ubuntu)

I have Googled and the problem is described, the problem is probably fixed in the latest apache2 version, but I have not found any solution for Feisty using the repositories with apt-get.

Is there a simple solution?

---

