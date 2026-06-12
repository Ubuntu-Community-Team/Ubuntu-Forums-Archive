---
title: "Apache2 error.log.1 meaning"
date: 2022-08-16
forum: General Help
---

### Post by cearlp2 on 2022-08-16
Can anyone explain what this error means?

[Mon Aug 15 15:19:31.588520 2022] [authz_core:error] [pid 33145] [client 195.96.137.4:63687] AH01630: client denied by server configuration: /var/www/html/server-status
[Tue Aug 16 00:00:01.278417 2022] [mpm_prefork:notice] [pid 1107] AH00171: Graceful restart requested, doing restart

---

### Post by SeijiSensei on 2022-08-16
Yes, you likely don't have a <Location> stanza for that URI that permits access.

First, make sure you have the status module enabled with
```
sudo a2enmod status
```
It should be enabled by default.

Next run "sudo nano /etc/apache2/sites-available/000-default.conf", or whatever file houses the configuration for the default virtual server, and add this stanza:
```

<Location /server-status>
Require ip your.ip.address
</Location>

```
You don't want to make this page public, so limit it to your ip address. Exit and save the file with Ctrl+X.

Finally, restart the server with
```
sudo systemctl restart apache2
```
and try again. Worked for me.

---

### Post by cearlp2 on 2022-08-17
Thanks you for the suggestion SeijiSensei, however it did not change anything. apachectl status returns:
www-browser: not found
'www-browser -dump [http://localhost:80/server-status](http://localhost:80/server-status)' failed.
Maybe you need to install a package providing www-browser or you
need to adjust the APACHE_LYNX variable in /etc/apache2/envvars

I tried it with -dump and --dump but get the same result.
My browser is Firefox 98.0.2

---

### Post by SeijiSensei on 2022-08-17
I thought you were trying to access the status page with a browser, not apachectl. I've not used that. Did you not try visiting your website with the /server-status URI after making the changes I suggested?

Perhaps the Apache manual page might help: [https://httpd.apache.org/docs/current/mod/mod_status.html](https://httpd.apache.org/docs/current/mod/mod_status.html)

---

### Post by cearlp2 on 2022-08-17
I can't access my website. Something has happened recently because the website has been actively working for months.
The only things I have found out is the error message I posted about and the last reply about apachectl status.

I don't understand what you mean by /server-status URl
Is the the 'URL of the website'/server-status?
In my case I tried 'localhost/server-status' and nothing happens...just finally times &#959;ut.

---

### Post by SeijiSensei on 2022-08-18
Well, if you can't access your website, you won't be able to connect via [http://localhost/server-status](http://localhost/server-status).

What do you see after
```

sudo systemctl restart apache2
sudo systemctl status apache2

```

Does it report any errors?

---

### Post by cearlp2 on 2022-08-18
SeijiSensei, The systemctl commands returned what looked normal for each command. Status was fine.
I got fed up with trying to find out why the LAMP stack wasn't working so I upgraded to 22.04, installed a new LAMP stack and things run just fine now.
Thanks for all the suggestions, I learned some things from your posts.

---

