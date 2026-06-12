---
title: "Ubuntu 12.04 LTS armhf preinstalled root password"
date: 2013-05-19
forum: General Help
---

### Post by Madswk on 2013-05-19
What is the default root pasword for the 'root' user?

Thank you,
Mads Kjeldsen

---

### Post by Hekabe on 2013-05-19
Unless that build is different, root is disabled by default. Use sudo to do admin tasks.

---

### Post by Madswk on 2013-05-19
Problem solved. I just removed the second parameter in the /etc/shadow file for the root.

---

