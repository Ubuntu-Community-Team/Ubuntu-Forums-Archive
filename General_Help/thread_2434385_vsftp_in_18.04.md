---
title: "vsftp in 18.04"
date: 2020-01-04
forum: General Help
---

### Post by cearlp2 on 2020-01-04
Is there something configuration wise that needs to be done to get vsftp to follow symlinks?
I have a symlink in the ftpuser's home directory that points to /var/www/html.
When I login as ftpuser and do an ls of html I get the list of /var/www/html but when I ftp to the server as ftpuser and do an ls I just get the /home/html file listed as a link to the /var/www/html directory.

---

