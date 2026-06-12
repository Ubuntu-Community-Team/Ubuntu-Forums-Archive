---
title: "Add php-fpm service alternative"
date: 2020-03-26
forum: General Help
---

### Post by bfuzze on 2020-03-26
Currently, my environment switches between php versions using update-alternatives.  This process updates version agnostic symlinks for various php related files, so I don't have specify the version.  However, when I need to restart php-fpm I still have to specify the version (e.g. sudo service php7.3-fpm restart).  Is there a way to modify the php update-alternatives configuration so that it creates/updates a symlink to the current php-fpm service?

I can foresee the end result looking something like...
(symlink) /etc/alternatives/php-fpm.service => /etc/init.d/php[active-version]-fpm
(symlink) /etc/init.d/php-fpm => /etc/alternatives/php-fpm.service
...but I don't know how to configure this through the update-alternatives architecture (or if its possible).

Thanks.

18.04.4 LTS (Bionic Beaver)

---

