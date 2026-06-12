---
title: "Problem accessing Apache2 and lampp folders"
date: 2023-03-17
forum: General Help
---

### Post by zargathronax on 2023-03-17
Good day everyone, currently i am working in ubuntu 22.10 and im having a peculiar situation. Im trying tu run some php code in a website, i try to use apache2 first but when i try to reach the folder (Using sudo nautilus)  nautilus close unexpectedly the same with lampp i click on "Open application folder" and when i try to navigate it closes again. Anyone has some recomendation for this?

---

### Post by pqwoerituytrueiwoq on 2023-03-17
the default location for web content in apace2 is [FONT=courier new]/var/www/html/[/FONT]
you need to have [FONT=courier new]libapache2-mod-php[/FONT] installed to run php

you will likely want to set [FONT=courier new]display_errors[/FONT] to [FONT=courier new]On[/FONT] in [FONT=courier new]/etc/php/*/apache2/php.ini[/FONT] (should be line 503)

it sounds like your file browser is crashing, check the output in your terminal, you could try a different file browser like [FONT=courier new]thunnar[/FONT]

i usually using [FONT=courier new]nano[/FONT] to edit files in a terminal

---

### Post by zargathronax on 2023-03-17
Well thunar works perfectly, indeed it was a problem with nautilus Anyways i used a sudo chmod 777 /var/www/html for putting my files there sadly, i dont see a way to make html a favorite folder in the sidebar. Thanks for the help

---

### Post by pqwoerituytrueiwoq on 2023-03-21
drag/drop it in to the side bar

you can just change the group
```
sudo chown root:$USER /var/www/html
sudo chmod 774 /var/www/html
```
this way random users and www-data can not edit your files (if you had a bad security hole in your code at least www-data will not be able to alter your data)

you could put a symlink to it in your home folder if needed
```
ln -s /var/www/html ./myLinktoHTML
```

---

### Post by TheFu on 2023-03-21
> **zargathronax said:**
> Well thunar works perfectly, indeed it was a problem with nautilus Anyways i used a sudo chmod 777 /var/www/html for putting my files there sadly, i dont see a way to make html a favorite folder in the sidebar. Thanks for the help

Whoa there Tex!  You are using a GUI to deploy files for a website?  Then you are using chmod 777?  Do you want to be hacked?

The best practice is to setup a deploy script that places the files into the live server area, sets the owner, group, permissions to be as restrictive as possible, optimizes and images BEFORE they are copied, and reloads the web server config (start/stop) to ensure all the updates are seen.  This script should run with the userid and group necessary, not any end-user's login.

---

