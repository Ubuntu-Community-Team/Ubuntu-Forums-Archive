---
title: "Default old MariaDB and dealing with it now when everything is set up"
date: 2020-09-30
forum: General Help
---

### Post by hiandyhi on 2020-09-30
I have Ubuntu 18.04 and I run

```
sudo apt install mysql-server
sudo mysql_secure_installation


```

Now it shows me I have MySQL 5.7 installed, which doesn't have REGEXP_REPLACE, which I need.

1. Why did it installed old version, how would I go with installing a MySQL 8 straight away?
2. How do I fix it now. When I already installed 5.7, have all data in, have everything running and update to 8+.

---

### Post by deadflowr on 2020-09-30
Your install command was for mysql-server not mariadb-server.

---

### Post by hiandyhi on 2020-09-30
> **deadflowr said:**
> Your install command was for mysql-server not mariadb-server.

I edited my mistake.

---

