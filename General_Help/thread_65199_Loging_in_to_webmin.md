---
title: "Loging in to webmin"
date: 2005-09-13
forum: General Help
---

### Post by Thulemanden on 2005-09-13
Webmin is not accept neither root nor user with the common user password.

How do I log in?

---

### Post by lao_V on 2005-09-13
During installation, webmin copies the root user and password into its own directory. Hence you need to have the root account enabled, which by default, is not in Ubuntu.

There's two ways you can rectify this now. Either by editing the webmin's user/password list, if you know where it is or uninstall webmin, enable root, and install it again.

---

