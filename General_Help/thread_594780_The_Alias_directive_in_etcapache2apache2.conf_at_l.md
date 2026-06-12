---
title: "The Alias directive in /etc/apache2/apache2.conf at line 129 will probably never matc"
date: 2007-10-28
forum: General Help
---

### Post by mitjab on 2007-10-28
#Let's have some Icons, shall we?
Alias /icons/ "/usr/share/apache2/icons/"
<Directory "/usr/share/apache2/icons">
    Options Indexes MultiViews
    AllowOverride All
    Order allow,deny
    Allow from all

    AddHandler mod_python .py
    PythonHandler mod_python.publisher
    PythonDebug On

</Directory>

what is wong here. I search but i did not find any solution.

---

