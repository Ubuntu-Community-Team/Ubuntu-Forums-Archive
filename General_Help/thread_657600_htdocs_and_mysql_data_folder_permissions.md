---
title: "htdocs and mysql data folder permissions"
date: 2008-01-03
forum: General Help
---

### Post by vugh on 2008-01-03
im trying to switch from windows to linux, i have a website and mysql database i want to move. i installed apache2, php, mysql and phpmyadmin thru synaptic. but...

i cannot copy html files folder htdocs/web1 to /var/www because permission denied
i cannot copy mysql data folder mysql/data/web1 to /var/lib/mysql because permission denied

i tried "chown"ing /var/www so i was able to copy (i "chown"ed to my_username). i want to do the same to /var/lib/mysql (currently, the owner is "mysql - MySQL Server") 

my question is, what are the implications for this (changing the owner to my_username)? am i doing the right thing? or is there another way around this? this is my first attempt at web development in linux, would appreciate all the help i can get.. thanks!

P.S.
since i was able to copy the htdocs/web1 folder, i tried [http://localhost/web1](http://localhost/web1) and i got "Forbidden: You don't have permission to access /web1/ on this server.".. what's wrong?

---

### Post by compwiz18 on 2008-01-03
Use sudo.  It makes life so much easier because you don't have to chown random directories :KS

I'd suggest you read this on sudo first: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

just do ```
sudo cp /file/1 /var/www/
``` or press alt+f2 at the same time, and enter ```
gksudo nautilus
```to get a graphical file browser. BE CAREFUL WITH THIS THOUGH; it will allow you to change ANYTHING on your system.

> P.S.
since i was able to copy the htdocs/web1 folder, i tried [http://localhost/web1](http://localhost/web1) and i got "Forbidden: You don't have permission to access /web1/ on this server.".. what's wrong?

I could be wrong, but changing the permissions on the /var/www directory may have screwed up letting the web server be able to read the files in there, hence giving the forbidden error.

---

### Post by vugh on 2008-01-03
great!!!! i changed the permissions and now everything works perfectly... thanks!!!!!!!!

---

### Post by vugh on 2008-01-04
oops... ive changed all the permissions to 777... but i can't INSERT, UPDATE, DELETE or do anything with my database. worse, it does'nt give any error. it reports the operations to be successful but nothing happens to the database.

what could be wrong?

---

