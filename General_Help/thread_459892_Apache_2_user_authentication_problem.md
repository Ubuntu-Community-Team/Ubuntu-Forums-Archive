---
title: "Apache 2 user authentication problem"
date: 2007-05-31
forum: General Help
---

### Post by rlwpub on 2007-05-31
I have a default LAMP install of Ubunto with Apache 2

I uploaded the following .htaccess file.

AuthUserFile /var/www/.htpasswd
AuthGroupFile /dev/null
AuthName SiteName
AuthType Basic

require valid-user

I also created a username in the .htpasswd file.

It is being ignored. The web page shows and I do not get the password challenge box.

What am I doing wrong?

Re's
Rob

---

### Post by fanatik on 2007-05-31
well usually the .htpasswd goes in the directory of the website you wish to protect, which might be the DocumentRoot of the website, which is normally /var/www/html/. Also you will need an appropriate AllowOverride directive for your Directory.

the AuthUserFile should be created with the htpasswd command.

See here for more info: [http://httpd.apache.org/docs/2.0/howto/auth.html]("http://httpd.apache.org/docs/2.0/howto/auth.html")

HTH

---

