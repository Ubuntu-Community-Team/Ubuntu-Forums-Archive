---
title: "Apache2"
date: 2020-12-01
forum: General Help
---

### Post by tech-jeff on 2020-12-01
Hi,

I'm installing a web service for an Ubuntu server with version 16.04.7 LTS. So I did the command

sudo apt install apache2

after installing, I seem can't find the httpd.conf file to edit the listening ports, server, etc. Am I missing something?

Thanks
Jeff

---

### Post by TheFu on 2020-12-01
16.04 support ends in a few months.
Today, the version to install is 20.04.

All apache config files are in /etc/apache2/ somewhere. There is no http.conf.  Are you using the right documentation?  I checked on a 16.04 apache install.

---

### Post by tech-jeff on 2020-12-01
Thanks, I saw an article after posting this

[https://ubuntu.com/tutorials/install-and-configure-apache#3-creating-your-own-website](https://ubuntu.com/tutorials/install-and-configure-apache#3-creating-your-own-website)

This might be really helpful

---

### Post by tech-jeff on 2020-12-01
Followed the guide above and I can't access the test homepage whether internal or external

---

### Post by tech-jeff on 2020-12-01
I can access the homepage through Ip but it still shows the default Apache homepage instead of the index.html which i created 
I edited the conf file which points to my index.html

     ServerAdmin <email>
     DocumentRoot  </var/www/<folder i created>
     ServerName <fqdn>

So this fqdn has a dns published through Godaddy and once I ping this it resolves using the public IP. and this public IP is NAT'ed to our internal server

---

### Post by TheFu on 2020-12-01
Post your complete conf file from the sites-enabled/ directory.  The file(s) in there should be symlinks to flies in sites-available/.  
This would be a good time to learn about symbolic links, if those are new.

What is posted above looks wrong. t needs to look more like a valid XML flie with open/close parts.

The docs on apache.org are valid. Just make sure you look at the same version

---

### Post by tech-jeff on 2020-12-01
Both sites-available and sites-enabled has the same <name.conf> files the only difference is the name.conf under sites-enabled is highlighted as mint green color but as I check the content, it shows exactly the same thing, here's a sample

company@hport:/etc/apache2/sites-available$ cat name.conf
<VirtualHost *:80>
        # The ServerName directive sets the request scheme, hostname and port that
        # the server uses to identify itself. This is used when creating
        # redirection URLs. In the context of virtual hosts, the ServerName
        # specifies what hostname must appear in the request's Host: header to
        # match this virtual host. For the default virtual host (this file) this
        # value is not decisive as it is used as a last resort host regardless.
        # However, you must set it for any further virtual host explicitly.
        #ServerName [www.example.com](www.example.com)


        ServerAdmin <email>
        DocumentRoot /var/www/<folder i created>
        ServerName company.domain.com


        # Available loglevels: trace8, ..., trace1, debug, info, notice, warn,
        # error, crit, alert, emerg.
        # It is also possible to configure the loglevel for particular
        # modules, e.g.
        #LogLevel info ssl:warn


        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined


        # For most configuration files from conf-available/, which are
        # enabled or disabled at a global level, it is possible to
        # include a line for only one particular virtual host. For example the
        # following line enables the CGI configuration for this host only
        # after it has been globally disabled with "a2disconf".
        #Include conf-available/serve-cgi-bin.conf
</VirtualHost>


# vim: syntax=apache ts=4 sw=4 sts=4 sr noet

Thanks
Jeff

---

### Post by TheFu on 2020-12-01
Think you are missing a Directory stanza nested inside the <VirtualHost .... > tags.

```
      <Directory /var/www/html > 
          DirectoryIndex index.html
      </Directory>
```

Also, the directory needs at least read permissions for the apache userid - that's the userid that apache processes run under.
Of course, this assumes you've watched the log files as you accessed the webserver and saw connections/errors.  If you don't see those lines added immediately, then it is very likely the issue is firewall or network related.

---

### Post by SeijiSensei on 2020-12-02
> **tech-jeff said:**
> Both sites-available and sites-enabled has the same <name.conf> files the only difference is the name.conf under sites-enabled is highlighted as mint green color but as I check the content, it shows exactly the same thing
"Enabling" a web site in Ubuntu (using the command a2ensite) creates a "symbolic link" in /etc/apache2/sites-enabled that points to the corresponding file in /etc/apache2/sites-available. Here is the default entry in sites-enabled:

```
lrwxrwxrwx 1 root root 35 Jun  7 10:48 000-default.conf -> ../sites-available/000-default.conf
```

The "files" are identical because you're looking at the target of the symbolic link if you display the entry in sites-enabled.

---

### Post by tech-jeff on 2020-12-08
I was able to make http worked but for some reason https or port 443 isn't working. I did allow this on ufw. Am I still missing something?

Thanks
TECH-JEFF

---

### Post by TheFu on 2020-12-08
HTTPS is significantly more complex and requires creating/requesting an SSL cert and configuring the site files appropriately. It isn't just opening and forwarding a port.  [https://httpd.apache.org/docs/2.4/ssl/ssl_howto.html](https://httpd.apache.org/docs/2.4/ssl/ssl_howto.html)

---

### Post by SeijiSensei on 2020-12-09
Did you try enabling the default SSL site with "sudo a2ensite default-ssl" and restarting the server as directed?

If you want to use SSL on sites of your own, you'll need certificates and the appropriate definitions in /etc/apache2/sites-available. For certificates, take a look at [Let's Encrypt]("https://letsencrypt.org/").

---

### Post by TheFu on 2020-12-09
I use Let's Encrypt for my non-commercial and personal websites.  Sometimes that is abbreviated as "LE".

You can create self-signed certs too, but since LE certs are free, nobody really does that anymore. I think the last self-signed cert I created was probably 3 yrs ago.  LE certs expire every 90 days, so they have automatic processes to renew.  When using apache (which I don't use for any public websites), I think most of the LE tools will do both the SSL cert request and modify the site-enabled/ file for you for trivial static websites. 

There are a few different tools that will request LE certs and handle things in the config files.  I use acme.sh because the LE tools didn't immediately work for my needs.

FYI, I think LE changed their top-level CA provider to one that isn't supported by older, unsupported, phones.   [https://hackaday.com/2020/12/01/lets-encrypt-will-stop-working-for-older-android-devices/](https://hackaday.com/2020/12/01/lets-encrypt-will-stop-working-for-older-android-devices/) will do a better job than I explaining the problem. I think my Nexus4 will break, but my newer devices will not.

---

### Post by SeijiSensei on 2020-12-09
I run a cron job overnight to check for certificate expiry.

```

# check for pending LetsEncrypt cert updates
43 03 * * * root /usr/local/bin/certbot-auto renew >> /var/log/httpd/certbot 2>&1 && service httpd restart > /dev/null 2>&1

```
(This is on a CentOS machine, but the basic idea doesn't depend on the distribution.)

---

