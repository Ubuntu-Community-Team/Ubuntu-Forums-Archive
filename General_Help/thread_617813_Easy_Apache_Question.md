---
title: "Easy Apache Question"
date: 2007-11-19
forum: General Help
---

### Post by rgfrancis on 2007-11-19
Ok, I am sure this question has been asked before, many times. I install Ubuntu and Apache and get everything working fine. Then I download Bluefish (I think that is what its called) to edit the index.html file I have in the default location for webpages. This default location was obviously setup by Apache. Now I can open the index.html file and edit it, but I cannot save it. I understand that the folder is locked down to the root user and I don't know how to change the permissions to that folder. Or should I change the Apache configuration file to point to another folder? And if so, how? Or is there a way to open Bluefish as the root user?

Thanks for your time.

---

### Post by rgfrancis on 2007-11-19
bump

---

### Post by juan@forum on 2007-11-19
you can change the user owner of the apache document root to your user

sudo chown -R user /var/www

then you will have the right permissions to edit and save the file

---

