---
title: "Partially disabled web server"
date: 2008-02-27
forum: General Help
---

### Post by afiore1961 on 2008-02-27
I setup ubuntu Dapper Drake with Apache, MySQL and PHP5  - however remotely I can only access the text of web pages - the  template (or CSS) do no show up. What did I do wrong - or have missed? Thanks

---

### Post by doublehelixer on 2008-02-27
Make sure you have libapache2-mod-php5 installed (for apache2), and check that the module is linked in the enabled modules in /etc/apache2

---

### Post by kool_kat_os on 2008-02-27
> **afiore1961 said:**
> I setup ubuntu Dapper Drake with Apache, MySQL and PHP5  - however remotely I can only access the text of web pages - the  template (or CSS) do no show up. What did I do wrong - or have missed? Thanks

on the pages with a link to the CSS did you put the correct directory?

---

