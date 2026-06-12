---
title: "Securing Apache 2.2.4 web server"
date: 2007-06-06
forum: General Help
---

### Post by Mayez on 2007-06-06
Hi,

i installed the apache 2.2.4 on the ubuntu but everybody can access it.
i need to secure it.

Can you please help me _to set a username and a password to the apache_ so only i can have the access to change it?

**What i need to know is that when i want to login to the web server, i want the security window to pop-up asking for a username and a password**

---

### Post by mlind on 2007-06-06
If you mean user authentication for your webserver, then try out basic authentication [http://httpd.apache.org/docs/2.2/howto/auth.html](http://httpd.apache.org/docs/2.2/howto/auth.html) and maybe change to SSL mode only.

---

### Post by Mayez on 2007-06-07
What i need to know is that when i want to login to the web server, i want the security window to pop-up asking for a username and a password.

what are the steps and the commands to do so?

---

### Post by indytim on 2007-06-07
If you want to run your LAMP as development only, this is from the WIKI

Change ports.conf so that it contains:

Listen 127.0.0.1:80


You will need to restart apache for it to be effective.

I've used this before (and currently).  Disclaimer : Had trouble with it in Feisty w/ standard LAMP build - unresolved at this point.

IndyTim

IndyTim

---

### Post by mlind on 2007-06-07
> **Mayez said:**
> What i need to know is that when i want to login to the web server, i want the security window to pop-up asking for a username and a password.

what are the steps and the commands to do so?

just follow the link I posted and setup Basic Authentication. It works in the way you describe.

```

        <Directory />
                Options FollowSymLinks
                AllowOverride None

                [B]AuthType Basic
                AuthName "By Invitation Only"
                AuthUserFile /etc/apache2/passwd/passwords
                Require valid-user[/B]
        </Directory>

```
and use **htpasswd** to generate entries */etc/apache2/passwd/passwords* file. Make sure the file is only readable by root and www-data.

---

