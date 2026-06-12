---
title: "Webmin from universe [Error - Invalid Password]"
date: 2005-05-08
forum: General Help
---

### Post by tonycubex on 2005-05-08
Trying to install Webmin (from universe), but when logging in, keep getting "Error - Invalid password. Password contains invalid characters." I've reset the webmin user account password but still does not work.

Any ideas?

Thanks

---

### Post by yusufk on 2005-08-26
Try:
# /usr/share/webmin/changepass.pl /etc/webmin root <your passwordhere>

---

### Post by zee on 2005-08-26
It worked for me as well.

tnx!
zee

---

### Post by bluegroper on 2005-09-03
Thx.  That worked for me too.

---

