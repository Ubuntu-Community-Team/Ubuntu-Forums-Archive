---
title: "VAR Permissions!?"
date: 2007-01-05
forum: General Help
---

### Post by mikeylikesit on 2007-01-05
I would like to set up a web server. I am using an older version of Ubuntu. Can anyone tell me how i can change the permissions in the VAR folder so that i can paste index.html into and delete everything else inside the folder? 

Any Help would be great 

Thanks

---

### Post by jpeddicord on 2007-01-05
Do you mean /var/www? You do **not** want to change anything in the var folder, that will break your system.

Anywho, to change the permissions of /var/www, type this into a terminal:
```
sudo chmod 777 /var/www
```

Jacob

---

### Post by mikeylikesit on 2007-01-05
do you have to log off and then log back on too to see the changes? It did not seem to work for me. 

is this all i have to put?   sudo chmod 777 /var/www

i want the user name "admin" to be able to access this folder 

so i need to put "admin" anywhere? 

Im new, so anyhelp is great

---

### Post by po0f on 2007-01-06
mikeylikesit,

I don't think you want to change the group owning /var/www to 'admin'.  Just note what it is now (ie, 'www-data').  Add your user to that group, and make sure 'www-data' has write permission on /var/www:
```
$ sudo gpasswd -a USER www-data
$ sudo chmod g+w -R /var/www
```
You'll have to log out for the changes to take effect.

---

