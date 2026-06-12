---
title: "Don't automatically start service after install"
date: 2007-03-31
forum: General Help
---

### Post by Apreche on 2007-03-31
Ubuntu has one very nice feature that it automatically starts any services after you install them. If you do apt-get install mysql-server, then after the installation is complete, the server will be started with the default configuration. 99% of the time, this is awesome. However, I am in a weird situation where I want to install services without having them automatically start. Is there a way to disable this functionality? I'm doing this on Dapper. Thanks.

---

### Post by Ramses de Norre on 2007-03-31
The starting is done by the post-installation script in the package, so you'll need to modify that script and build a new package. (Or maybe file-roller can modify files within packages.)

---

