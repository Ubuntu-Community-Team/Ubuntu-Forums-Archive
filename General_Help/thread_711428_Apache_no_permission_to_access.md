---
title: "Apache no permission to access"
date: 2008-02-29
forum: General Help
---

### Post by SpikeyMike on 2008-02-29
Hi, I installed apache2 on ubuntu and followed this how-to:

[https://help.ubuntu.com/community/ApacheMySQLPHP?highlight=%28apache%29#head-67cb901b98d8dd3892cec7ebf48e961c6f19467f](https://help.ubuntu.com/community/ApacheMySQLPHP?highlight=%28apache%29#head-67cb901b98d8dd3892cec7ebf48e961c6f19467f)
 
but when I try to connect using the browser I get the following message:

[COLOR="Red"]Forbidden

You don't have permission to access /index.html on this server.
Apache/2.2.4 (Ubuntu) Server at 192.168.1.11 Port 80[/COLOR]

can anyone please advise me about this, I am new to apache......

---

### Post by iwarp62 on 2008-02-29
Hey, i believe your issue is one of two things, i'm not really sure which.

I'm not sure apache actually comes with a default index.html page in ubuntu because i can't remember. Thats ok though, try doing a quick:

```
cd /var/www/
ls
```

This will give you a listing of what is in apache's root directory (ie... what you see when you go to [http://localhost](http://localhost)).

If you see an index.html then it has the wrong permissions, so the fix for that would just be:

```
sudo chown www-data /var/www/index.html
```

If you didn't see an index.html, then it doesn't exist. Your server is trying to show it even though it's not there.

You could create it by running:

```
sudo gedit /var/www/index.html
```

and pasting your html into there. Good Luck!

---

### Post by SpikeyMike on 2008-03-01
Hi, thanks for your reply, I did what you said and managed to get it partially working, it displays my homepage but not as it should look, there is also a css document in the folder that is used by the homepage so I changed the permissions on that too and on the folder containing the images but it still doesn't display as it should, how can I change permissions on the /var/www folder itself?

Also something I don't understand, when I open the httpd.conf file it is empty, any ideas about that?

Mikey

---

### Post by piotroxp on 2008-07-18
> **SpikeyMike said:**
> Hi, thanks for your reply, I did what you said and managed to get it partially working, it displays my homepage but not as it should look, there is also a css document in the folder that is used by the homepage so I changed the permissions on that too and on the folder containing the images but it still doesn't display as it should, how can I change permissions on the /var/www folder itself?

Also something I don't understand, when I open the httpd.conf file it is empty, any ideas about that?

Mikey

What worked for me :
<Directory "/YOUR_DIR_WHERE_HTTPD_RESIDES/httpd/htdocs">
  BLA BLA BLA HERE
    Order allow,deny
    Allow from 127.0.0.1 <<
    Allow from localhost <<
</Directory>

and then 

# If you wish httpd to run as a different user or group, you must run
# httpd as root initially and it will switch.  
#
# User/Group: The name (or #number) of the user/group to run httpd as.
# It is usually good practice to create a dedicated user and group for
# running httpd, as with most system services.
#
User daemon
Group daemon

User YOUR_USER_NAME
Group YOUR_USER_NAME

works fine. about the empty httpd.conf -> just rebuild it ;) of course, I presume you hold your sites in /httpd/htdocs ;)

---

