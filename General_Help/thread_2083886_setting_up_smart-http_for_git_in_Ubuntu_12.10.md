---
title: "setting up smart-http for git in Ubuntu 12.10"
date: 2012-11-13
forum: General Help
---

### Post by t1279k on 2012-11-13
Hi

I want to setup smart-http for git in Ubunto 12.10. according to doc i have to do some changes in Httpd.conf in apache. But in Ubuntu it is seems to be different. There is no httpd.conf in /etc/apache2 folder

Am i suppose to update this
SetEnv GIT_PROJECT_ROOT /var/www/git
SetEnv GIT_HTTP_EXPORT_ALL
ScriptAlias /git/ /usr/libexec/git-core/git-http-backend/

in apache2.conf?

---

