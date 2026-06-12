---
title: "Apache2 webroot directory"
date: 2008-04-11
forum: General Help
---

### Post by tommyhakinen on 2008-04-11
Hi,

i am new to apache in linux. I have gutsy desktop version installed along with LAMP. I am using my laptop to learn PHP and website. i am having problem to edit my files in the default webroot directory (/var/www). I am thinking of changing it to my home directory (example /home/user/www). I tried to change the /var/www to /home/user/www. but when i move my files in to /home/user/www, i got error message stating i have no permission to access the files in the server. Is there anything i can do to correct this?

thanks

best regards,

tommy

---

### Post by comandrei on 2008-04-12
You can set the DocumentRoot to be your /home/user/www  in /etc/apache2/sites-available/default by chaging /var/www in /home/user/www
Then you should
 ```

sudo usermod -G www-data user
chown -R user:www-data /home/user/www

```
that should do it

---

### Post by Rhubarb on 2008-04-12
You could also make a symbolic link to your ~/www directory
```
sudo ln -s /var/www/ ~/www/
```
This should do it.

---

### Post by fragos on 2008-04-12
> **Rhubarb said:**
> You could also make a symbolic link to your ~/www directory
```
sudo ln -s /var/www/ ~/www/
```
This should do it.

Where do you place this link?

I checked out the man pages for usermod and it said that -G and the code as offered will delete all group memeberships other than www-data. Very scary. Loosing admin group membership in particular would paint you in a corner.

---

### Post by tommyhakinen on 2008-04-12
Thank you for the replies. I am going to try it.

---

