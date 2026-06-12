---
title: "Folder Permission Problems"
date: 2007-09-24
forum: General Help
---

### Post by Zatarg on 2007-09-24
Hi :)

I have installed Apache2, MySql, MySql-Server, phpmyadmin and php5

```
sudo aptitude install apache2 php5 mysql phpmyadmin 
```
Read from the post: [http://ubuntuforums.org/showthread.php?t=553567&highlight=xampp]("http://ubuntuforums.org/showthread.php?t=553567&highlight=xampp")
Then i went back and read the rest (maybe shoulda read it all first ;P)

and added ```
sudo aptitude install mysql-server
```

however, i cannot put any files in the var/www folder.
Ive tried chmod-ing it and chown-ing it. but nothing seems to change it.
eg: ```
 sudo chmod 0777 /var/www
```

Any ideas on how to get myself (and other users) able to create and edit files in the folder?

Cheers ;)

---

### Post by FunkyJack on 2007-09-24
To put files and edit you can use:

```
sudo nautilus
```

If you need to edit often then it's faster to change the owner.

---

### Post by Zatarg on 2007-09-24
Thanks,

After executing that, i navigated to the folder and changed the permissions via properties...

This seems to have worked to the extend that I can edit the files.

However, no other users seem to be able to, and it took a few tries before this stuck.

Any other ideas? :)

---

### Post by FunkyJack on 2007-09-24
You should make a new group for that users and make them members of that group.
After that just give that new group permissions.

---

### Post by Zatarg on 2007-09-25
Cool, that seems to have worked ;)

Cheers ;)

---

