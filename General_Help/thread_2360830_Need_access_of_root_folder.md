---
title: "Need access of root folder"
date: 2017-05-09
forum: General Help
---

### Post by uzumakifahim on 2017-05-09
Hi, 

I've installed open cart on my PC. Now I need to install some plugins or extensions using the url via a browser i.e. localhost/site/something. Unfortunately, when I am trying to access and click on the install button, it is giving me the following error :

```
This installer needs to modify some OpenCart files. Please check write access for following files of your opencart store :
-/admin/controller/module
-/admin/view/template/module

```

How can I access those files with admin privileges via web browser? Please suggest. Thanks in advance.

---

### Post by TheFu on 2017-05-09
Doubt you can change permissions through a browser.

Show the **ls -l -/admin/controller/module -/admin/view/template/module**  BTW, I think the file/directory names are wrong. That leading '-' is probably wrong.  Most websites are located under /var/www/ ... somewhere.

You will probably need ssh and sudo access.

File and directory permissions are the core to all system security on Unix systems. It is very important to have a complete understand of these things, especially if you are running any services.  Ubuntu has a guide: [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)  If you spend 45 minutes today, you'll save hours, weeks, months, years of frustration.

---

