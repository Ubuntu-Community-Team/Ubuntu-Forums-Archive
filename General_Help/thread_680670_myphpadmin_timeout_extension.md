---
title: "myphpadmin timeout extension?"
date: 2008-01-28
forum: General Help
---

### Post by swigrid on 2008-01-28
Could somebody give me an advice how to change or (the best) disable TIMEOUT in myPHPAdmin?

Thanx

---

### Post by gvartser on 2008-01-28
Edit phpMyAdmin's config.inc.php and add or update LoginCookieValidity the value as follows:

```
$cfg['LoginCookieValidity'] = 3600 * 9; // 9 hours
```

/g

---

### Post by Rick Z on 2008-02-13
Where can I find the config.inc.php files?  Also, how can I enable the SSL in phpmyadmin?

Thanks!

---

