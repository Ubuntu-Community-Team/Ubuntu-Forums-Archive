---
title: "apache permission www-data"
date: 2014-10-01
forum: General Help
---

### Post by Matteo_Martinelli on 2014-10-01
Hi guyz!
I have some problem with the permission of the user www-data.
Particularly, when apache create a file via PHP (like cache file), I can't remove that through, for instance, rm command.

Someone know how I can solve this problem?

Thank you.

---

### Post by SeijiSensei on 2014-10-01
Use sudo.

---

### Post by mcduck on 2014-10-01
...or add yourself to the *www-data* group.

---

### Post by SeijiSensei on 2014-10-01
> ...or add yourself to the www-data group. 

You will need to grant write privileges to the www-data group in /var/www/html and to any of the files it contains.
```

cd /var/www
sudo chmod g+w html
cd html
sudo chmod g+w *

```

Personally I generally don't let the www-data user or its group members write anything into /var/www/html.  That opens up sites to defacement.

---

