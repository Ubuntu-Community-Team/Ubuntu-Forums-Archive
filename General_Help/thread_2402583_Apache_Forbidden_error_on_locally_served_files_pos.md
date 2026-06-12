---
title: "Apache Forbidden error on locally served files: post upgrade ubuntu 16.04 to 18.04"
date: 2018-10-02
forum: General Help
---

### Post by silverspr on 2018-10-02
Hello, I've googled myself into a stupor trying to fix this. Background: in-place upgrade of Ubuntu 16.04 to 18.04, my previously working web application Seeddms broke, throwing the Apache 403 Forbidden error.  (Seeddms was working under ubuntu 16.04). This lead to the discovery no local web pages were being served. I've created a very simple locally served web page that throws the same error but will be much easier to troubleshoot...or so I hope. Apache 2.4 on both Ubuntu 16.04 and 18.04 (so none of this makes sense).

```
Apache.conf
<Directory />
    Options FollowSymLinks
    AllowOverride None
    Require all denied
</Directory>

<Directory /usr/share>
    AllowOverride None
    Require all granted
</Directory>

<Directory /var/www/>
    Options Indexes FollowSymLinks
    AllowOverride All
    Require all granted
</Directory>

Testme.conf (Alias Virtual host file):
    Alias "/test" "/home/user/testme"
    <Directory "/home/user/testme">
            Directory Index index.php index.html    
            Require all granted
    </Directory>

    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined

/home/user/testme folderpermissions:
-rwxrwxr-x 1 user www-data 11 Oct  1 20:30 index.html

/var/www/html permissions
-rw-r--r-- 1 www-data www-data 11321 Nov 13  2017 index.html 
```
(I've tried various permutations, user www:data, chmod +x ... none have worked.  There seems to be a plethora of different ideas on how to configure this folder.)

thank you for any and all insight
the only other alternative is a fresh install of 18.04
Forbidden

 [HR][/HR]You don't have permission to access /test on this server.

  Apache/2.4.29 (Ubuntu) Server at localhost Port 80

---

### Post by spjackson on 2018-10-02
What are the permissions on the folders needed to access /home/user/testme/index.html? i.e.
```

ls -ld /home /home/user /home/user/testme

```
User www-data needs execute on /home and /home/user and read+execute on /home/user/testme (I think).

---

### Post by silverspr on 2018-10-02
Thank you...I had to set the user group owner to www-data...you nailed it!!

---

### Post by hgkrug1 on 2019-06-20
I experience the same problem. I have tried to to use the User and Groups GUI to give me access to www-data. I have also tried the proposed solution at [https://serverfault.com/questions/124800/how-to-setup-linux-permissions-for-the-www-folder](https://serverfault.com/questions/124800/how-to-setup-linux-permissions-for-the-www-folder) but problem persists?

This error occurs with both Firefox and Chromium. It does not occur with Midori web browser? I cleare the cash of Firefox as well after changes were made.

Would you be so kind to be more specific in how "set the user group owner to www-data"?

This issue is even more complicated. I reproduce the error on my Mac with Firefox and Safari. Here is the search I do: [https://ubuntuforums.org/search.php?searchid=20187291](https://ubuntuforums.org/search.php?searchid=20187291)

Thanks!
Gert Kruger

---

