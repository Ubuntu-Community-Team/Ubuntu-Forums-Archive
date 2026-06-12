---
title: "Ubuntu change sudo php path"
date: 2014-01-04
forum: General Help
---

### Post by giannhs905 on 2014-01-04
I was struggling with apache2 already installed in ubuntu so I decided to return back to lampp..I have unistalled apache 2 mysql server and phpmyadmin.
The problem is that when I type sudo which php I get nothing...
So I cannot request e.g. sudo composer create-project laravel/laravel.....since php is missing for root user..

Although when I type which php I get /opt/lampp/bin/php..


Is it possible to make the root user use the same path..?

---

### Post by TheFu on 2014-01-05
This is a security feature for sudo. Rather than modifying how the PATH is used in sudo, perhaps setting up a specific version of php to be used by sudo would make more sense?

**man sudoers** will explain more details.  There are multiple ways to solve this - Command Environment section is a start and the Cmnd_Alias option is another.

Most people use 0.000001% of what sudo was created to handle.

---

