---
title: "symbolic link for Apache files?"
date: 2017-04-22
forum: General Help
---

### Post by garyed on 2017-04-22
I want to link my Apache directory from one Ubuntu version to another so my localhost will be the same on either version I boot into.  I deleted my html folder on the new version so I just had /var/www then did  ```
ln -s /media/me/Ustudio/var/www/html  /var/www/html 
```
Now the new /var/www/html link/folder shows all my files just like the old version does but when I try to get to localhost in my browser it gives me "Forbidden don't have permission" error. I am the owner of both files & have permissions when I check in the terminal so I'm lost at what to do next.
Any ideas?

---

### Post by SeijiSensei on 2017-04-23
In the <Directory> stanza for this virtual host add
```

<Directory ...>
    Options All
    [stuff]
</Directory>

```
By default Apache will not follow symbolic links.  You can either use "[Options]("https://httpd.apache.org/docs/2.4/mod/core.html#options") All" or "Options FollowSymLinks" to permit links.

---

### Post by garyed on 2017-04-23
> **SeijiSensei said:**
> In the <Directory> stanza for this virtual host add
```

<Directory ...>
    Options All
    [stuff]
</Directory>

```
By default Apache will not follow symbolic links.  You can either use "[Options]("https://httpd.apache.org/docs/2.4/mod/core.html#options") All" or "Options FollowSymLinks" to permit links.

I'm assuming the file you're talking about editing is apache2.conf. I've tried both Options All & Options FollowSymlinks on all the different  <Directory>....... </Directory> places in apache2.conf & it still doesn't work.  I tried rebooting & it still doesn't work. I made sure the partition I'm linked to is mounted & everything shows properly in the file browser when I click on the symlink. It just gives me the same error that I  "**don't have permission to access / on this server**".

---

### Post by SeijiSensei on 2017-04-23
No, by default the relevant file is /etc/apache2/sites-available/000-default.conf.  That defines the default virtual server.  Don't touch any other files like apache2.conf.  Have you read the documentation for how Ubuntu structures the Apache server directories?  See [https://help.ubuntu.com/lts/serverguide/httpd.html](https://help.ubuntu.com/lts/serverguide/httpd.html)

In 000-default.conf, add the following under the DocumentRoot entry:
```

<Directory "/var/www/html">
     Options All
</Directory>

```

---

### Post by garyed on 2017-04-23
> **SeijiSensei said:**
> No, by default the relevant file is /etc/apache2/sites-available/000-default.conf.  That defines the default virtual server.  Don't touch any other files like apache2.conf.  Have you read the documentation for how Ubuntu structures the Apache server directories?  See [https://help.ubuntu.com/lts/serverguide/httpd.html](https://help.ubuntu.com/lts/serverguide/httpd.html)

In 000-default.conf, add the following under the DocumentRoot entry:
```

<Directory "/var/www/html">
     Options All
</Directory>

```

Thanks for the help but i still can't make it work. My DocumentRoot entry is  /var/www/html  so I added the code just below that. I restarted Apache & after it still didn't work I tried changing the  <Directory "/var/www/html"> to <Directory "/ "> since  /var/www/html  was already my DocumentRoot but that didn't work either. I know my server works if I don't use a symlink but I don't want to have to copy everything over & have two different sets of the same files which might get confusing especially when editing web sites.

---

### Post by SeijiSensei on 2017-04-23
What is the specific error recorded in /var/log/apache2/error.log?

---

### Post by garyed on 2017-04-24
This is the error that keeps showing up:
> [Sun Apr 23 23:59:01.472051 2017] [core:error] [pid 10962] [client ::1:54108] AH00037: Symbolic link not allowed or link target not accessible: /var/www/html
[Sun Apr 23 23:59:01.512927 2017] [core:error] [pid 10962] [client ::1:54108] AH00037: Symbolic link not allowed or link target not accessible: /var/www/html, referer: [http://localhost/](http://localhost/)


---

### Post by garyed on 2017-04-24
Could there be something wrong with the way I did the symlink? 
Here's what it looks like in the terminal from /var/www
> gary@gary-U16:/var/www$ ls -l
total 0
lrwxrwxrwx 1 gary gary 32 Apr 22 21:07 html -> /media/gary/Ustudio/var/www/html


---

### Post by garyed on 2017-04-24
The problem was in the permissions of the parent directory "/media/gary" where the link was pointing.     There were no "r,w,x " for others & I just did  "chmod o+x gary"  & it works.  I had "x" permissions all the way through  Ustudio/var/www/html  so I didn't think the parent directory would matter but evidently it did. The complete path was "/media/gary/Ustudio/var/www/html"
Thanks again for all the help.

---

